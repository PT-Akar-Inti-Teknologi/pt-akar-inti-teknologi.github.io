---
layout: default
title: Code Review
permalink: /standards/code/code-review
parent: Coding Standards
grand_parent: Standards
nav_order: 2
---

# Code Review Standard

## Why

A structured code review process ensures code quality, security, and maintainability. It also supports team learning, prevents technical debt, and helps catch issues early before code reaches production.

---

## Code Review Checklist

Every pull request must be reviewed with reference to the following points:

1. **Code Standards and Structure**
   - Ensure code follows the established style guide and architecture standards.
   - Refer to internal documentation (e.g., Backend | AIT IT Knowledge Base).

2. **Potential Bugs and Security Vulnerabilities**
   - Inspect for possible logical errors, security loopholes, or anti-patterns.
   - Ensure sensitive data is not exposed and authentication/authorization is handled properly.

3. **Algorithm Quality, Performance, and Efficiency**
   - Assess efficiency and resource usage, especially for critical paths.
   - Utilize agreed tools (e.g., profiler, static analysis) for performance review.

4. **Readability and Documentation**
   - Code should be easy to read and understand.
   - Variable and function names must be descriptive.
   - Document complex business logic with clear comments or additional documentation if needed.

5. **Test Coverage and Effectiveness**
   - Confirm the presence and relevance of unit and/or integration tests for all major code changes.
   - Ensure tests cover both positive and negative cases where possible.

6. **No Duplicated Code or Dead Code**
   - Check for any duplicate logic, unused functions, or commented-out code.
   - Remove unnecessary or obsolete code.

7. **No Hardcoded Credentials or Sensitive Data**
   - Verify that passwords, API keys, and secrets are not present in code or logs.
   - Ensure usage of configuration files or environment variables.

8. **Formatting and Linting**
   - All code should pass linting and formatting checks before review.
   - Follow project pre-commit or CI standards if any.

---

## Reviewer Assignment and Approval Policy

- Each pull request must be reviewed by at least one developer other than the author.
- Self-merge is strictly prohibited.
- Only the Tech Lead or a designated reviewer (with Tech Lead approval) may perform the final merge into protected branches.
- All review comments and required changes must be addressed before merging.

---

## Code Review SLA

- Reviews should be performed within 1 business day whenever possible.
- Large pull requests (> 500 lines of code) should be split into smaller PRs, or a notice should be given in the PR description.

---

## Review Process Best Practices

- Use a clear and respectful tone when giving feedback.
- Always provide reasoning or references when requesting changes.
- Avoid excessive nitpicking; focus on code quality, security, and business logic.

---