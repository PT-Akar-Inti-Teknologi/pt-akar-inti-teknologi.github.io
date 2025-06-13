---
layout: default
title: HTTP Codes
permalink: /standards/backend/http-codes
parent: Backend
grand_parent: Standards
nav_order: 3
---

# HTTP Status Code Convention

## Purpose

Proper use of HTTP status codes is essential for building reliable and maintainable REST APIs. These codes allow client applications to understand the result of an HTTP request and handle responses accordingly. Misuse of status codes can lead to misleading behavior and poor error handling.

---

## Error Handling Codes

### 400 - Bad Request

Used when:
- The request is syntactically correct but semantically invalid.
- Required fields are missing or invalid.
- Input fails validation (e.g., invalid email format, negative values).

Avoid returning 200 with an error message in the body. Instead, always validate input and return 400 with a structured error response.

### 404 - Not Found

Used when:
- The requested resource does not exist.
- The endpoint is correct, but the ID or path parameter refers to a non-existent resource.

Do not use 404 for incorrect endpoints or misrouted paths; those should return 400 or 405.

### 409 - Conflict

Used when:
- The request could not be completed due to a conflict in the current state of the resource.
- Example: attempting to create a resource with a unique field that already exists (e.g., duplicate email, username).

---

## Authentication & Authorization Codes

### 401 - Unauthorized

Used when:
- No authentication token is provided.
- The authentication token is invalid or expired.

Clients may retry after refreshing tokens. This code indicates that the request has not been applied because it lacks valid authentication credentials.

### 403 - Forbidden

Used when:
- Authentication is valid, but the user does not have permission to perform the requested operation.
- Common for access control failures (e.g., valid token but no role or permission).

Do not use 403 for expired or missing tokens-use 401 instead.

---

## Success Codes

### 200 - OK

Used when:
- The request has succeeded.
- The response includes the requested data.

Typically used for GET, PUT, or POST (when returning resource info).

### 204 - No Content

Used when:
- The request has succeeded, but there is no content to return.
- Common for DELETE operations or successful updates with no response body.

Avoid using 204 if the client expects a body or metadata.

---

## Server Error

### 500 - Internal Server Error

Used when:
- An unexpected server-side error occurs.
- Typically indicates unhandled exceptions, null pointer errors, or downstream service failure.

Never expose internal exception messages to clients. Always log detailed error stack traces on the server and return generic messages to the client.

---

## Additional Notes

- Use **405 Method Not Allowed** when an endpoint exists, but the HTTP method is not supported (e.g., `PUT` on a `GET-only` route).
- Use **422 Unprocessable Entity** as an alternative to 400 for semantically correct but invalid input (e.g., business rule violation).
- Return consistent error formats across all APIs, including `code`, `message`, and `details` if needed.

