---
layout: default
title: Repository Name
permalink: /standards/repository/name
parent: Code Repository
grand_parent: Standards
nav_order: 1
---

# Repository Name

## Why

Clear and consistent repository names allow developers to:
- Quickly find existing projects as references
- Understand project context from its name
- Align naming across departments (e.g., CRM, QA, DevOps)

## Naming Convention

Use this format:

```
<client_code>_<project_code>_<domain>_<platform>[_<module>]
```

### Components:
- `client_code`: Short code that identifies the client or organization. Must align with CRM or internal codes.
- `project_code`: Unique name for the project. Should be consistent across divisions.
- `domain`: Logical domain such as `web`, `admin`, or `mobile`.
- `platform`: Indicates platform or stack, such as:
  - `backend`
  - `frontend`
  - `mobile` (for hybrid apps like Flutter)
  - `android`
  - `ios`
- `module`: Optional. Used for microservice architecture or modular monoliths.

## Rules

- Use all lowercase
- Use underscores `_` as separators
- Avoid using dashes `-`, camelCase, or PascalCase
- Keep the name descriptive yet concise

## Examples

| Use Case                   | Repository Name                    |
|----------------------------|------------------------------------|
| Web backend                | `jhd_web_backend`                  |
| Web frontend               | `jhd_web_frontend`                |
| Admin panel backend        | `jhd_admin_backend`               |
| Admin panel frontend       | `jhd_admin_frontend`              |
| Mobile app (Flutter)       | `jhd_mobile`                       |
| Native Android             | `jhd_mobile_android`              |
| Native iOS                 | `jhd_mobile_ios`                  |
| Microservice - Auth        | `jhd_web_auth_backend`            |
| Microservice - Product     | `jhd_web_product_backend`         |

## Anti-Patterns (Do NOT use)

```
- AIT-JIRA
- JIRA_AIT
- AitJiraWeb
- crmWebsite
```

These violate casing, structure, or naming consistency.

## Notes

For multi-repo setups:
- Keep naming consistent across related services
- Align naming with deployment targets and monitoring dashboards
