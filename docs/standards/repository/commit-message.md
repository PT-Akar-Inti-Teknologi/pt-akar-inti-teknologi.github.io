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
- A simple navigation through git history (e.g: ignoring style changes)
- Automatic generation of the changelog
- Commit based CI/CD pipeline step (e.g: don't trigger build and deploy if the change is only about documentation or styling)

## Convention

Use the following format,

```markdown
type(scope): [Task ID] subject

body
```

`type` is mandatory and must be one of the following:

- `feat`: A new feature
- `fix`: A bug fix
- `build`: Build related changes (eg: npm related/ adding external dependencies)
- `chore`: A code change that external user won't see (eg: change to .gitignore file or .prettierrc file)
- `docs`: Documentation related changes
- `refactor`: A code that neither fix bug nor adds a feature. (eg: You can use this when there is semantic changes like renaming a variable/ function name)
- `perf`: A code that improves performance
- `style`: A change that is related to code style or lint (e.g: fix indentation, missing semicolons or whitespaces)
- `test`: Adding new test or making changes to existing test

`scope` is optional and must follow these rules:

- A phrase describing parts of the code affected by the change. For example "(seeder)" or "(middleware)"
- Small caps with dash (-) as separator. For example "(web-server)" or "(storage-service)"
- It can be empty when the change is a global or difficult to assign to a single component, in which case the parentheses are omitted

`Task ID` is mandatory for type `feat`,`fix` and `refactor` and must follow these rules:
- The Task ID can be obtained from Bitrix cards or Jira issues
- The Task ID is used to identify the relationship between the commit message and the corresponding Bitrix card or Jira issue that is being worked on

`subject` is mandatory and must follow these rules:

- In English
- Use a single space after colon
- A single sentence only
- Imperative, present tense (eg: use "add" instead of "added", "adding" or "adds")
- Don't use dot (.) at the end
- Don't capitalize first letter

`body` is optional and must follow these rules:

- In English
- Use a blank line to separate with the subject
- Used only when further explanation is required or change contains several parts
- Maximum 72 characters
- Use bullet points if needed
- Multi line is ok
- Capitalize is ok

## Examples

```
fix(middleware): [DUMMY-1] ensure Range headers adhere more closely to RFC 2616
```

```
feat(store): [DUMMY-1] add multi shift support to store operational hours

- Modify Update Store Operational Hours API endpoint
- Update query list store to support multi shift
```

```
feat(storage): [DUMMY-1] add AWS S3 support
```

```
refactor: [DUMMY-1] move all auth functionalities to a separate module
```

```
chore: release 2.0.1
```

```
build: bump axios to 0.21.1
```

```
style: replace CRLF to LF
```
