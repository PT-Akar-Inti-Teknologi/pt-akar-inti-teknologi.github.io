---
layout: default
title: API Convention
permalink: /standards/backend/api-convention
parent: Backend
grand_parent: Standards
nav_order: 1
---

# API Convention

## Why

To provide consistent developer experience across APIs and ensure maintainability over time, all names used in an API should be:

- Simple
- Intuitive
- Consistent

## Common Conventions

- Use plural nouns for resource names.
- Use kebab-case (`-`) for URL path segments. Avoid using underscores (`_`) in URIs.
  - Example: `/inventory-management/managed-entities/{id}/install-script-location`
- Use lowercase letters in all URL paths.
- Resource names should represent nouns, not verbs.
  - Example: `/user-management/users` or `/device-management/managed-devices/{device-id}`

## Query Parameters

- Use snake_case for query parameters to distinguish them from kebab-case paths.
- Standard query parameters:
  - `search`: keyword search across multiple fields. Example: `?search=John Doe`
  - `sort`: format `?sort=field,asc|desc`. Example: `?sort=name,desc`
  - `page`: pagination index (starting from 0). Example: `?page=0`
  - `size`: page size. Example: `?size=10`

Example:
```
/device-managements/managed-devices?region_area=USA&brand=XYZ&sort=installation-date
```

## Header Parameters

Use kebab-case (lowercase with dashes) for custom headers.

| Correct Usage       | Incorrect Usage     |
|---------------------|---------------------|
| `x-token-access`    | `X_Token_Access`    |
| `ait-project-id`    | `ait_project_id`    |
| `user-profile-id`   | `User_Profile_ID`   |

## Versioning (Recommended)

- Use URI-based versioning when necessary: `/v1/users`
- Alternatively, support header-based versioning for advanced control:
  - `Accept: application/vnd.ait.v1+json`
- Clearly document the versioning strategy per service.

## Endpoint Naming Principles

Group APIs by logical resources (nouns) and apply actions using appropriate HTTP methods.

### 1. Standard CRUD Example

For resource `tickets`:

| Method | Endpoint        | Action                      |
|--------|-----------------|-----------------------------|
| GET    | /tickets        | List all tickets            |
| GET    | /tickets/{id}   | Get ticket by ID            |
| POST   | /tickets        | Create a new ticket         |
| PUT    | /tickets/{id}   | Update ticket               |
| DELETE | /tickets/{id}   | Delete ticket               |

### 2. Resource Relations (Parent-Child)

Use nested structure when the relation only makes sense within the parent context:

| Method | Endpoint                        | Description                        |
|--------|----------------------------------|------------------------------------|
| GET    | /posts/{id}/comments            | List comments of a post            |
| POST   | /posts/{id}/comments            | Add comment to a post              |
| GET    | /posts/{id}/comments/{cid}      | Get specific comment               |
| PUT    | /posts/{id}/comments/{cid}      | Update a comment                   |
| DELETE | /posts/{id}/comments/{cid}      | Delete a comment                   |

### 3. Actions Outside of Standard CRUD

For actions not easily mapped to CRUD semantics:

| Method | Endpoint                              | Description                        |
|--------|----------------------------------------|------------------------------------|
| POST   | /users/{id}/resend-verification       | Resend verification email          |
| POST   | /devices/{id}/restart                 | Restart device                     |
| POST   | /carts/{id}/checkout                  | Checkout a cart                    |

Use clearly documented actions when RESTful mapping is not practical, such as global `/search` endpoint.
