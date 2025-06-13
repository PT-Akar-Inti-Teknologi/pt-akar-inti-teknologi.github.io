---
layout: default
title: Code Security
permalink: /standards/code/code-quality
parent: Coding Standards
grand_parent: Standards
nav_order: 2
---

# Coding Security Standard

This standard outlines the minimum secure coding practices that must be applied in all projects. The goal is to reduce common vulnerabilities and ensure code is robust, safe, and auditable.

---

## 1. Input Validation & Sanitization

All input from users, external sources, or other systems must be validated and sanitized. Always use a whitelist (accept only expected fields and formats) rather than a blacklist (block only certain fields).

**Correct Example (Node.js using Joi):**
```javascript
const schema = Joi.object({
  email: Joi.string().email().required(),
  age: Joi.number().integer().min(18)
});
const result = schema.validate(req.body);
if (result.error) throw new Error("Invalid input");
```

**Incorrect Example:**
```javascript
// Accepting all incoming fields and no format validation
const email = req.body.email;
```

Best Practice:  
Use schema-based validation libraries and sanitize input before further processing.

---

## 2. Authentication & Authorization

All endpoints that require authentication must verify the user's identity using secure methods (JWT, OAuth2, or similar). Authorization checks must be applied for every resource access, even for internal APIs.

**Correct Example:**
- Validate JWT signature for every request.
- Check user roles/permissions before allowing access.

**Incorrect Example:**
- Trusting a user ID from the client without verifying a token.
- Skipping authorization on internal endpoints.

Best Practice:  
Never trust any identifier or claim from the client unless it has been verified by the backend.

---

## 3. Sensitive Data Handling

Sensitive information such as passwords, secret keys, tokens, and financial data must never be logged, hardcoded, or stored in plaintext.

**Correct Example:**
- Store passwords using strong hashing (bcrypt/argon2).
- Use environment variables for credentials.
- Mask or omit sensitive fields in application logs.

**Incorrect Example:**
- Storing plaintext passwords in the database.
- Committing API keys or secrets into the source code.
- Logging full payloads including passwords.

Best Practice:  
Always audit your code and configuration for sensitive data exposure.

---

## 4. SQL Injection & NoSQL Injection Prevention

Always use parameterized queries or ORM/ODM features to avoid injection vulnerabilities.

**Correct Example:**
```javascript
// Using parameterized query
db.query("SELECT * FROM users WHERE email = $1", [userInput]);
```

**Incorrect Example:**
```javascript
// Directly interpolating user input into query string
db.query("SELECT * FROM users WHERE email = '" + userInput + "'");
```

Best Practice:  
Never concatenate user input into queries.

---

## 5. Cross-Site Scripting (XSS) Prevention

Escape all user-generated output before rendering in HTML. Do not use functions such as `innerHTML` or `eval` with untrusted data.

**Correct Example:**
- Use textContent instead of innerHTML for DOM updates.

**Incorrect Example:**
- Updating DOM via innerHTML using raw input from users.

Best Practice:  
Apply output encoding and use sanitizer libraries as needed.

---

## 6. Cross-Site Request Forgery (CSRF) Protection

Implement CSRF protection for all state-changing operations. Use CSRF tokens or set SameSite cookie attributes for authentication cookies.

**Correct Example:**
- Use middleware (e.g., csurf for Express) to validate CSRF tokens.
- Set cookies with `SameSite=Strict` for sensitive sessions.

**Incorrect Example:**
- No CSRF protection on forms that update user data.

Best Practice:  
Always protect endpoints that modify data from unauthorized cross-site requests.

---

## 7. File Upload Security

Validate the type, size, and content of uploaded files. Store files outside the web root and rename files on upload.

**Correct Example:**
- Accept only specific file types (e.g., images).
- Scan files for malware before processing.
- Store uploaded files in a non-public directory.

**Incorrect Example:**
- Allowing any file type or extension to be uploaded.
- Storing files with their original names in a public directory.

Best Practice:  
Always treat uploaded files as potentially dangerous.

---

## 8. Security Headers

Set HTTP security headers such as Content-Security-Policy, X-Content-Type-Options, X-Frame-Options, and X-XSS-Protection.

**Correct Example (Express):**
```javascript
const helmet = require('helmet');
app.use(helmet());
```

**Incorrect Example:**
- Not setting any security-related headers.

Best Practice:  
Use a middleware or server config to apply recommended security headers.

---

## 9. Error Handling & Logging

Do not expose stack traces, database errors, or internal system details to the user. All error details must be logged securely and only generic messages shown to end users.

**Correct Example:**
- Log error details with context for developers, show generic message to user.

**Incorrect Example:**
- Sending raw stack trace or database error message to the client.

Best Practice:  
Use a centralized logging solution, and redact sensitive information in logs.

---

## 10. Dependency & Third-Party Library Management

Keep all dependencies up to date. Regularly scan dependencies for vulnerabilities.

**Correct Example:**
- Use tools like npm audit, Snyk, osv-scanner in CI/CD.
- Avoid dependencies that are deprecated or unmaintained.

**Incorrect Example:**
- Using packages with known vulnerabilities and no security patches.

Best Practice:  
Review and update dependencies as part of the release process.

---

## 11. Transport Layer Security

All data transfers must use HTTPS/TLS. Do not accept unencrypted traffic.

**Correct Example:**
- Enforce HTTPS on all environments.
- Redirect HTTP to HTTPS.

**Incorrect Example:**
- Allowing plain HTTP connections to backend or API.

Best Practice:  
Reject all non-encrypted connections at the application or infrastructure level.

---

## 12. Session & Token Security

Store tokens and session cookies securely. Set Secure and HttpOnly flags, and always set expiration.

**Correct Example:**
- Use HttpOnly, Secure, and SameSite attributes for cookies.
- Expire tokens after a defined period.

**Incorrect Example:**
- Storing tokens in localStorage without expiration or flags.
- Setting long-lived tokens or never expiring sessions.

Best Practice:  
Rotate tokens and session secrets regularly.

---

## 13. Rate Limiting & Brute Force Protection

Apply rate limiting to sensitive endpoints such as login or password reset. Monitor failed attempts and block or delay as needed.

**Correct Example:**
- Use rate limiter middleware on authentication endpoints.

**Incorrect Example:**
- No rate limiting; unlimited failed login attempts allowed.

Best Practice:  
Implement rate limiting and alerting for brute force attempts.

---

## 14. Security Testing

Regularly run static and dynamic security tests. Integrate security testing tools in CI/CD pipeline.

**Correct Example:**
- Use static analysis tools (SAST) and dynamic testing tools (DAST) on every build.

**Incorrect Example:**
- No automated security testing, manual testing only at release.

Best Practice:  
Schedule periodic penetration testing and review findings promptly.

---

## References

- OWASP Top Ten
- Secure Coding Practices Checklist (OWASP)
- Node.js Security Handbook
- Google Web Security Guidelines

---