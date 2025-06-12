---
layout: default
title: Branch Name
permalink: /standards/repository/branch
parent: Code Repository
grand_parent: Standards
nav_order: 4
---

# Branch Name

## Why

Git offers flexible branching strategies which are very useful for collaboration and CI/CD automation. However, using inconsistent naming conventions can lead to confusion and difficulty maintaining codebases.

> **Important:** No one is allowed to push directly to main branches like `main`, `staging`, `development`, or `production`. These branches can only be updated via **Pull Request**.

## Branch Types

There are two kinds of branches: **Regular Branches** and **Temporary Branches**.

---

## Regular Branches

These are permanent branches in the repository:

- `main`: The production branch. Always stable. No direct commits allowed. Changes must come from PRs from other branches such as `staging`.
- `staging`: Used for QA, UAT, and automation testing before changes are pushed to production.
- `development`: The default development branch where all code is integrated. Prefer PRs over direct commits.

Other permanent branches may be added (e.g., for specific environments or platforms). When doing so:

- Keep names short: `ubuntu20`, not `for-server-with-ubuntu-version-20`
- Use dashes `-` for separators
- Ensure it's truly permanent—otherwise, use a temporary branch instead

---

## Temporary Branches

Created for specific tasks and removed after merging. Use the format:

```
<group>/<task-id>-description
```

### Group Prefixes

| Group      | Purpose                                                       |
|------------|---------------------------------------------------------------|
| `feat`     | New features                                                  |
| `bugfix`   | Bug fixes or QA findings                                      |
| `hotfix`   | Urgent fixes for production                                   |
| `experiment` | Tryouts with new libraries, tools, or architectures         |
| `wip`      | Work-in-progress that may be incomplete or shared with others |

### Task ID

- Include task ID if available (e.g., JIRA ticket)
- Use dash `-` to separate multiple IDs
- Example: `feat/DEMO-1234-DEMO-4567-login`

### Description Rules

- Use **lowercase** only: `bugfix/login-error`, not `BugFix/LoginError`
- Be concise: `feat/operational-hours`, not `feat/implementing-store-operational-hours`
- Use **nouns**: `feat/ldap-integration`, not `feat/integrates-ldap`
- Use **dashes** `-` as word separators

---

## Examples

| Use Case                          | Branch Name                                 |
|----------------------------------|---------------------------------------------|
| Feature for login screen         | `feat/DEMO-1234-login`                      |
| Fix for broken query             | `bugfix/DEMO-5678-invalid-query`           |
| Hotfix for payment crash         | `hotfix/DEMO-9012-payment-crash`           |
| WIP for redesign                 | `wip/redesign-ui`                           |
| Experimental refactor            | `experiment/new-cache-strategy`            |
| Multi-ticket feature             | `feat/DEMO-1111-DEMO-2222-store-summary`   |
