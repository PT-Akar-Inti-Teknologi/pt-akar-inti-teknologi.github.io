---
layout: default
title: Database
permalink: /standards/backend/database
parent: Backend
grand_parent: Standards
nav_order: 4
---

# Database Convention & Best Practices

## Why

Consistency in database naming and design simplifies collaboration, improves performance, and reduces debugging effort. Standards prevent hidden issues and make maintenance easier.

---

## Database Naming Convention

- Use lowercase and underscore for database names, e.g. `ait_app_db`.
- For multi-environment:
  - Development: `{project}_dev`, e.g. `crm_dev`
  - Staging: `{project}_stg`, e.g. `crm_stg`
  - Production: `{project}_prod`, e.g. `crm_prod`
- For microservices, prefix or suffix with service name, e.g. `orders_service_prod`.
- Avoid generic names like `test`, `db`, or `data`.

---

## Table & Column Naming

### Tables

| Recommended Practice           | Avoid                | Notes                          |
|-------------------------------|----------------------|--------------------------------|
| Plural names: `users`, `orders` | `user`, `tbl_user`   | Avoid prefixes like `tbl_`     |
| lower_snake_case: `order_items` | `OrderItems`         | Keep naming consistent         |
| Collective names: `employees`    | Vague singular       | Clearly represents contents    |
| Primary key as `id`, foreign as `xxx_id` | `uid`, `id_user` | Simple and consistent          |

### Columns

| Recommended Practice              | Avoid                   | Notes                   |
|-----------------------------------|-------------------------|-------------------------|
| Singular column: `name`, `created_at` | Duplicating table name    | Avoid redundancy        |
| All lowercase                     | `CreatedAt`, `Created_At` | Consistency is key      |
| Boolean with `is_`: `is_active`   | `active`, `verified`    | Boolean intent is clear |
| ENUM for static values            | Numeric status           | Easier to maintain      |
| DB-level `CHECK` constraints      | Only application-side    | Validation at DB safer  |

---

## Timestamp & Audit Columns

- Add `created_at`, `updated_at`, `deleted_at` with `timestamp with time zone`.
- Add `created_by`, `updated_by`, `deleted_by` for audit if needed.
- Use default values (`now()`) and triggers where possible.
- Consider `row version` (optimistic locking) for concurrency.

---

## Query Optimization Guidelines

- Use `EXPLAIN` or `EXPLAIN ANALYZE` for slow queries.
- Avoid `SELECT *`, select only needed columns.
- Avoid subqueries and large aggregations unless necessary.
- Avoid using functions in `WHERE` on indexed columns.
- Use `LIMIT` for large datasets.
- Apply cache for heavy queries (TTL at least 1 minute when possible).

### Indexing

- Add indexes for columns used in `JOIN`, `WHERE`, or `ORDER BY`.
- Avoid too many indexes; impacts write speed and storage.
- Composite indexes should match query order.

#### Common Index Use Cases

| Scenario             | Example                                   |
|----------------------|-------------------------------------------|
| WHERE clause         | `SELECT * FROM orders WHERE status = 'pending'` (`status`) |
| JOIN conditions      | `JOIN users ON users.id = orders.user_id` (`orders.user_id`) |
| ORDER BY             | `ORDER BY created_at DESC` (`created_at DESC`) |
| WHERE + ORDER BY     | `WHERE user_id = ? ORDER BY created_at DESC` (`user_id, created_at DESC`) |
| GROUP BY/aggregates  | `GROUP BY status` (`status`)              |
| DISTINCT queries     | `SELECT DISTINCT status FROM orders` (`status`) |

#### Indexing Anti-patterns

| Scenario                | Example                                  |
|-------------------------|------------------------------------------|
| Low-cardinality column  | Index on boolean like `is_active`        |
| Frequently updated      | Index on `updated_at`                    |
| Unused columns          | Index on internal/debug fields           |
| Wrong composite order   | Index `(a, b)` for `WHERE b=? AND a=?`  |
| Indexing all columns    | High-write tables                        |

#### Tips

- Use `EXPLAIN` to check index usage.
- Partial indexes for subset of rows (PostgreSQL).
- Covering indexes for heavy reads.
- Review and clean up unused/duplicate indexes periodically.

---

## ORM Considerations

- Always review generated SQL from ORM.
- Use `EXPLAIN` to check real execution plan.
- Avoid eager loading unless justified.
- Prevent N+1 queries with proper loading strategy.
- Use parameter binding to prevent SQL injection.

---

## Migration, Seeding, and Access Control

- Use structured migration tools (Flyway, Liquibase, ORM-based).
- Seed scripts must be idempotent, avoid truncating important data.
- Developers should not have `DROP`, `TRUNCATE`, or `SUPER` privileges on production.
- Audit all schema (DDL) and data change (DML) in production.
- Isolate access roles for dev, staging, and prod.

---

## Data Management & Batch Processing

- Use batch operations for large `DELETE`/`INSERT` (with `LIMIT`).
- Archive old/inactive data to separate tables.
- Partition large tables (>10 million rows).
- Avoid long-held locks.

---

## Monitoring & Performance Tools

- Enable and monitor slow query logs.
- Use tools: `pg_stat_statements` (PostgreSQL), `performance_schema` (MySQL), or APM.
- For complex queries, prefer raw SQL over ORM when needed.

---

## Stored Procedure

Stored procedures are discouraged unless:
- Performance cannot be achieved in application layer.
- Logic is reused by multiple consumers of the same DB.
- Strict access control required at database level.

Prefer lightweight SQL functions or keep core logic in application/services.

---

## Race Condition & Locking Strategy

### Why It Matters

Race conditions can cause data inconsistency if concurrent changes are not managed. Use locking only when needed, and choose the right strategy for the scenario.

### Locking Types

- Pessimistic: Locks row immediately (`SELECT ... FOR UPDATE`)
- Optimistic: Uses version checking (update only if version unchanged)

| Use Case                  | Locking Strategy   |
|---------------------------|-------------------|
| Stock checkout, banking   | Pessimistic       |
| Profile update, reports   | Optimistic        |

Tips:
- Avoid long transactions  
- Use timeout and retry logic  
- Monitor locking with DB tools

---