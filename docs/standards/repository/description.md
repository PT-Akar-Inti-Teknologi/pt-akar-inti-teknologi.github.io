---
layout: default
title: Repository Description
permalink: /standards/repository/description
parent: Code Repository
grand_parent: Standards
nav_order: 2
---

# Repository Description

## Why

Repository names are often limited in length (e.g., 40 characters on GitHub), so the **description field** (or "Project Description") is essential to:
- Clarify the full meaning behind abbreviated or compact repository names
- Improve repository discoverability via search
- Provide immediate context without needing to open the repository

## Description Format

Use the following structure:

```
<Project Name> - <Main Technology or Framework> [ - <Programming Language> ]
```

### Guidelines

- **Describe the full repository name**.  
  For example, for `ait_jira_report_backend`, write:  
  `"AIT Jira Report Backend"`  
  This clarifies what `ait`, `jira_report`, and `backend` stand for.

- **Mention the primary technology or framework used.**  
  Example: `"AIT Jira Report Backend - Spring Boot"`  
  This helps filtering repos by tech like Spring Boot, Laravel, Angular, etc.

- **Optionally include the programming language** if multiple languages are possible.  
  Example: `"Mobile Order App - Swift"` vs `"Mobile Order App - Objective C"`

## Examples

| Repository Name               | Description                                          |
|------------------------------|------------------------------------------------------|
| `ait_jira_report_backend`    | AIT Jira Report Backend - Spring Boot - Kotlin      |
| `crm_mobile_ios`             | CRM iOS App - Native - Swift                        |
| `crm_mobile_android`         | CRM Android App - Native - Kotlin                   |
| `jhd_web_auth_backend`       | JHD Web Auth Backend - NodeJS - TypeScript          |
| `jhd_web_frontend`           | JHD Web Frontend - Angular                          |
