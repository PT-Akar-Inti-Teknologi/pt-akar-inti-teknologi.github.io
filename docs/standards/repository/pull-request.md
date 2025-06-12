---
layout: default
title: Pull Request
permalink: /standards/repository/pull-request
parent: Code Repository
grand_parent: Standards
nav_order: 5
---

# Pull Request Template

## Why

A consistent pull request template helps ensure:
- A standard structure is followed in every PR
- The purpose of changes is clearly communicated
- Code reviews are more effective and faster
- Team collaboration is improved and more efficient

## When to Use

Apply this structure to every pull request. If the repository is scoped per platform (e.g., frontend/backend/mobile), there is no need to repeat the platform in the PR description.

## Pull Request Title

Follow this format:

```

[PROJECT-123] Create Promo API Endpoint
```

**Guidelines:**

- Start with `[TICKET-ID]` to link with your issue tracker
- Use descriptive, active sentence
- Avoid vague titles like "Fix bug" or "Update code"
- Capitalize words properly, excluding short prepositions

**Examples:**

- `[APP-2341] Implement Promo Feature for Admin Panel`
- `[APP-2342] Fix Upload Bug in File Migration`
- `[APP-2380] Refactor Promo Validation Logic`
- `[APP-2390] Add Logging for Failed Upload Requests`

## Template Structure

### Task Reference

Link the PR with related task(s):

```
> [PROJECT-123] - Implement Create Promo API
> [PROJECT-124] - Fix Upload Bug in Migration
```

### Description

Briefly describe:

- What was changed
- Why this change is necessary

Example:

```
Implemented create promo API required for marketing campaign.
Fixed bug where uploaded file path was `undefined` due to incorrect file naming logic.
```

### Acceptance Criteria

- [ ] Name field must not be empty
- [ ] Password must be at least 6 characters
- [ ] Uploaded file must be saved successfully

### Changelog

- Added new endpoint: POST /promos
- Refactored upload logic for better file path handling
- Added name length validation to promo creation

### How to Test

Provide testing instructions:

```bash
POST /v1/admins/promos
{
  "title": "Year-End Promo",
  ...
}
```

Checklist:

- [ ] Tested locally
- [ ] Tested in staging
- [ ] Verified no regression to existing features

### Screenshots or Evidence (Optional)

Before / After comparison or new UI components:

![before]( ... image ...)
![after]( ... image ... )

### Additional Notes (Optional)

Any assumptions, edge cases, or dependencies that the reviewer should be aware of.

### References (Optional)

- Figma Design: [https://www.figma.com/file/xxxxx](https://www.figma.com/file/xxxxx)
- Depends on: #123, #456

---

## Full Example

```
Title:
[APP-2341] Implement Promo Feature for Admin Panel

Task Reference:
> [APP-2341] - Implement Promo Feature
> [APP-2342] - Fix Upload Error on Staging

Description:
Implemented promo creation API as part of the marketing module and fixed a bug in the file upload system.

Acceptance Criteria:
- [x] Email must be unique
- [x] Promo name cannot be empty
- [x] Uploaded image must be valid format

Changelog:
- Added endpoint: POST /v1/admins/promos
- Fixed upload file name logic
- Updated validation rules for promo name

How to Test:
1. Send POST request to /v1/admins/promos
2. Check for success response and saved data
3. Attempt to upload invalid files and verify error handling

Screenshots:
(before and after UI images)

Notes:
- Fallback validation added for optional image upload
- Related backend schema already deployed

References:
- Figma: https://www.figma.com/file/xxxxx
- Depends on: #2339
```
