---
layout: default
title: Commit Message
permalink: /standards/repository/commit
parent: Code Repository
grand_parent: Standards
nav_order: 4
---

# Commit Message

## Why

Using a structured commit message format ensures:
- Easier navigation through Git history (e.g., skip style-only commits)
- Automated changelog generation using tools like semantic-release
- Smarter CI/CD pipelines that skip deploys for non-code changes

## Convention Format

```text
type(scope): [TASK-ID] subject

body
```

### `type` (Required)

Use one of the following values:

| Type      | Description                                      |
|-----------|--------------------------------------------------|
| `feat`    | A new feature                                     |
| `fix`     | A bug fix                                        |
| `build`   | Build-related changes (dependencies, tooling)    |
| `chore`   | Maintenance changes invisible to users           |
| `docs`    | Changes to documentation                         |
| `refactor`| Code improvement without changing behavior       |
| `perf`    | Performance improvements                         |
| `style`   | Code formatting, whitespace, semicolons, etc.    |
| `test`    | Adding or updating tests                         |

### `scope` (Optional)

- Describes the part of the codebase being changed
- Format: lowercase with dashes (e.g., `web-server`, `auth-module`)
- Omit parentheses if the change is global or unscoped

### `TASK-ID` (Required for `feat`, `fix`, `refactor`)

- The Task ID is typically from Jira or Bitrix (e.g., `DEMO-1234`)
- Use square brackets: `[DEMO-1234]`
- For multiple task IDs, separate with commas: `[DEMO-1234, DEMO-5678]`
- Always use dash format (`DEMO-1234`), not `DEMO1234`

### `subject` (Required)

- Must be in English
- Use a single space after the colon
- Use imperative present tense (e.g., "add", not "added" or "adding")
- No punctuation at the end
- Do not capitalize the first letter

### `body` (Optional)

- Use if the commit contains complex or multi-part changes
- Separate from subject with a blank line
- Max line length: 72 characters
- Use bullet points for clarity
- Capitalization allowed

## Tooling Recommendation

Use the following tools to enforce this convention:
- [commitlint](https://commitlint.js.org/)
- [husky](https://typicode.github.io/husky/)
- [semantic-release](https://semantic-release.gitbook.io/)

## Examples

```text
fix(middleware): [DEMO-1234] ensure Range headers follow RFC 2616
```

```text
feat(store): [DEMO-1234] add multi-shift support to store hours

- Modify Update Store Operational Hours API endpoint
- Update query list store to support multi-shift
```

```text
feat(storage): [DEMO-1234, DEMO-4567] add AWS S3 support
```

```text
refactor: [DEMO-1234] move all auth functionalities to separate module
```

```text
chore: [DEMO-1234] release 2.0.1
```

```text
build: [DEMO-1234] bump axios to 0.21.1
```

```text
style: [DEMO-1234] replace CRLF with LF
```
