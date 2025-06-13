---
layout: default
title: Code Writing
permalink: /standards/code/code-quality
parent: Coding Standards
grand_parent: Standards
nav_order: 1
---

# Code Writing Standards

## 1. Clean Code Principles

### 1.1. Use Descriptive and Consistent Naming

Use clear and self-explanatory names for functions, variables, and classes. Avoid generic or ambiguous names such as `getData` or `process`. Always use names that describe the purpose and responsibility of the item.

**Correct Examples:**
- `getCustomerById(customerId)` — The function explicitly states it retrieves a customer using an ID.
- `calculateMonthlyReport(transactions)` — Indicates the function calculates a monthly report.

**Incorrect Examples:**
- `getData()` — The function does not specify what data is being retrieved.
- `process()` — Unclear what is being processed.

Best Practice:  
Follow language or framework naming conventions (CamelCase for JavaScript/Java, snake_case for Python, PascalCase for Classes).

---

### 1.2. Single Responsibility Principle

Each function or method should have one clear responsibility. Do not create functions that perform multiple unrelated actions.

**Correct Examples:**
- `validateUser(user)` — Only validates the user data.
- `calculateTransaction(items)` — Only calculates the total transaction.

**Incorrect Examples:**
- `validateAndSaveUser(user)` — Performs both validation and database operations.
- `calculateAndExport(data)` — Calculates and exports in a single function.

Best Practice:  
Break down large or multi-purpose functions into smaller, focused units. This makes testing, maintenance, and debugging easier.

---

### 1.3. Enforce Code Formatting and Linting

Always use automated tools such as linter and formatter (e.g., ESLint, Prettier, Black, Dart Format) to maintain consistent code style across the team.  
Integrate formatting and linting into your CI/CD pipeline or as pre-commit hooks (using Husky, lint-staged, or equivalent).

**Correct Example:**
- Codebase always formatted automatically on commit.

**Incorrect Example:**
- Manual formatting and inconsistent code style between files.

Best Practice:  
Include formatting and linting setup in your project’s onboarding documentation.

---

### 1.4. Avoid Magic Numbers and Hardcoded Values

Do not write hardcoded values directly in the code. Use constants or configuration files for any value that could change or needs to be referenced in multiple places. Constants should be named descriptively and written in uppercase.

**Correct Example:**
```javascript
const MAX_RETRY = 3;
if (retries > MAX_RETRY) { ... }
```
**Incorrect Example:**
```javascript
if (retries > 3) { ... }
```
Best Practice:  
Put constants in dedicated files or environment variables for configuration.

---

### 1.5. Apply the DRY (Don't Repeat Yourself) Principle

Avoid duplicate code. Reuse logic by extracting repeated code into functions, utility modules, or shared components.

**Incorrect Example:**
```javascript
// The calculation logic is repeated in both functions
function calculateDiscount(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += items[i].price * 0.1;
  }
  return total;
}
function printDiscount(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += items[i].price * 0.1;
  }
  console.log(total);
}
```

**Correct Example:**
```javascript
function getTotalDiscount(items) {
  return items.reduce((total, item) => total + item.price * 0.1, 0);
}
function printDiscount(items) {
  const total = getTotalDiscount(items);
  console.log(total);
}
```
Best Practice:  
Review your code for repeated logic regularly and refactor when needed.

---

### 1.6. Proper Error Handling

Handle all errors explicitly. Never display raw system or internal error details to end users.

**Correct Example:**
```javascript
try {
  // application logic
} catch (error) {
  showUserError("An unexpected error occurred. Please try again later.");
  logError(error); // Save detailed error log for debugging
}
```
**Incorrect Example:**
```javascript
try {
  // application logic
} catch (error) {
  alert(error); // Shows stack trace or internal message to user
}
```
Best Practice:  
Use centralized error handlers or middleware in both frontend and backend frameworks. Ensure error boundaries are implemented in React, or global exception filters in NestJS, Express, or Django.

---

## 2. Error Handling Policy

### 2.1. User-Facing Error Messages

Always use generic, non-specific error messages for end users. Avoid exposing which field or operation failed in detail.

**Correct:**
- "Invalid username or password."

**Incorrect:**
- "User not found."
- "Password is incorrect."
- "Email format invalid."

Best Practice:  
Group error responses where possible to prevent information disclosure, following OWASP recommendations.

---

### 2.2. Use Error Codes

Assign error codes to each error response to help support and development teams identify and troubleshoot issues efficiently.

**Example:**
```json
{
  "error_code": "AUTH-0001",
  "message": "Invalid username or password."
}
```
Best Practice:  
Document all error codes and meanings in your API documentation.

---

### 2.3. Hide System/Internal Errors

Never display technical details such as stack traces, timeout errors, or database exceptions to users.

**Correct Example (User sees):**
- "Sorry, something went wrong. Please try again later."

**Incorrect Example (User sees):**
- "Axios timeout"
- "PostgreSQL connection failed"
- "Stack trace: ..."

Best Practice:  
Always log full error details internally (log file or monitoring tools) but keep user messages simple and friendly.

---

## 3. Input and Payload Validation

### 3.1. Frontend Validation

Validate all user input in the frontend before sending to the backend, to provide fast feedback and reduce invalid requests.

**Validation should include:**
- Data format (e.g., email, phone number, numeric)
- Required fields
- Length and pattern (regex) constraints
- Logical constraints (e.g., date range, allowed values)

**Correct Example:**
```javascript
if (!email.includes("@")) {
  showError("Please enter a valid email address.");
}
if (!username) {
  showError("Username is required.");
}
```

---

### 3.2. Avoid Data Injection

Do not allow the client to send data that should be managed by the backend. For example, do not send product names or prices if those are in the database; send only the product ID.

**Correct Example:**
```json
{
  "product_id": "UUID"
}
```
**Incorrect Example:**
```json
{
  "product_id": "UUID",
  "product_name": "Injected Name"
}
```
Best Practice:  
Always use IDs or references to master data, and never trust client-supplied descriptive or calculated values.

---

### 3.3. Backend Validation Is Mandatory

Regardless of any client-side validation, backend must always re-validate all input to protect against manipulation and exploitation.

**Backend validation must cover:**
- Data validity (type, format)
- Data existence and consistency (exists in master data/database)
- User authorization to access or modify the data

**Correct Example:**
```typescript
if (!isValidUUID(req.body.product_id)) {
  throw new BadRequestException("Invalid product ID.");
}
const product = await productRepo.findById(req.body.product_id);
if (!product) {
  throw new NotFoundException("Product not found.");
}
if (!user.hasAccess(product)) {
  throw new ForbiddenException("Access denied.");
}
```

**Incorrect Example:**
- Accepting payload from client without further validation or checks.
- Relying only on frontend validation.

Best Practice:  
Use schema validation libraries (e.g., Joi, Yup, class-validator) and always verify data existence and permissions in backend business logic.

---