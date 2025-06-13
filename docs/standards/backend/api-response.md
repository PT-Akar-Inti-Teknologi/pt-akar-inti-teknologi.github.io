---
layout: default
title: API Response
permalink: /standards/backend/api-response
parent: Backend
grand_parent: Standards
nav_order: 2
---

# API Response Standard

## Why

Consistent API response structure:
- Enables easier frontend integration
- Supports better automated testing and documentation
- Improves error handling and observability
- Helps consumers understand the context of each response

## General Rules

All API responses must follow the structure below, regardless of success or error state:

```json
{
  "response_schema": {
    "response_code": "PROJECT-MODULE-CODE",
    "response_message": "string"
  },
  "response_output": <object | array | null>
}
```

- `response_schema` is always required
- `response_output` can be `null` on error responses
- Use consistent key casing (snake_case or camelCase – pick one per project)

> In a microservice context, `MODULE` may refer to the service name (e.g., `AUTH`, `ORDER`, `PAYMENT`). Ensure it's unique and consistent across services for traceability.

---

## Response Code Convention

### Format
```
<PROJECT_CODE>-<MODULE>-<CODE>
```

- `PROJECT_CODE`: Code for the system (e.g., `DEMO`)
- `MODULE`: Logical module or service name (e.g., `LOGIN`, `ORDER`, `AUTH`)
- `CODE`: Either HTTP status code or business code

### Examples

| Type           | Example               | Meaning                        |
|----------------|-----------------------|--------------------------------|
| HTTP Code      | `DEMO-LOGIN-200`      | Successful login               |
| Business Code  | `DEMO-LOGIN-00001`    | Invalid password               |
| HTTP Code      | `DEMO-ORDER-500`      | Server error in order service |
| Business Code  | `DEMO-AUTH-00002`     | Invalid token in auth service |

---

## HTTP Status Usage

| HTTP Code | When to Use                         |
|-----------|-------------------------------------|
| 200       | Success                             |
| 400       | Validation errors                   |
| 401       | Unauthorized                        |
| 403       | Forbidden                           |
| 404       | Not found                           |
| 406       | Not acceptable                      |
| 422       | Semantic error                      |
| 500       | Internal server error               |

---

## Recommended Additions for Long-Term Maintainability

Include these optional but recommended fields under `response_schema` for better debugging and traceability:

- `timestamp`: ISO 8601 timestamp of the response
- `request_id`: Unique identifier for correlating request logs

Example:

```json
"response_schema": {
  "response_code": "DEMO-LOGIN-0000",
  "response_message": "Sukses",
  "timestamp": "2025-06-12T09:32:12+07:00",
  "request_id": "123456789abcdef"
}
```

---

## Success Responses

### Single Data
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-0000",
    "response_message": "Sukses"
  },
  "response_output": {
    "detail": {
      "data_A": "aaaa",
      "data_B": "bbbb"
    }
  }
}
```

### Collection Data
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-0000",
    "response_message": "Sukses"
  },
  "response_output": {
    "list": {
      "pagination": null,
      "content": [
        { "data_A": "aaaa", "data_B": "bbbb" },
        { "data_A": "aaaa", "data_B": "bbbb" }
      ]
    }
  }
}
```

### Collection with Pagination
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-0000",
    "response_message": "Sukses"
  },
  "response_output": {
    "list": {
      "pagination": {
        "page": 0,
        "size": 10,
        "total_pages": 10,
        "total_elements": 100
      },
      "content": [
        { "data_A": "aaaa", "data_B": "bbbb" },
        { "data_A": "aaaa", "data_B": "bbbb" }
      ]
    }
  }
}
```

---

## Error Responses

### Validation Error
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-00001",
    "response_message": "Parameter tidak valid"
  },
  "response_output": {
    "errors": [
      { "field": "email", "message": "email format not valid" },
      { "field": "price", "message": "must be numeric" }
    ]
  }
}
```

### Not Found / Invalid Process
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-404",
    "response_message": "User tidak ditemukan"
  },
  "response_output": null
}
```

### Server Error
```json
{
  "response_schema": {
    "response_code": "DEMO-LOGIN-500",
    "response_message": "Internal server error"
  },
  "response_output": null
}
```
