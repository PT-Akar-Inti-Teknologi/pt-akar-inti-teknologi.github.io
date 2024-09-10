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

Having a consistent GitHub pull request template is important to ensure that each pull request follows a standardized format, clarifies its purpose, facilitates code review, and enhances team collaboration efficiency.

## Description

If using bitrix as task management, every pull request must begin with `> [#{task_id}] - {platform} - {comment/status}` in the description

- task_id: Task ID, found in bitrix URL or Jira Issue.
- platform: must follow these options:

platform | 
---|
BE |
FE Web |
FE CMS |
Mobile Android |
Mobile IOS |

- comment/status: short description of status of the task.

## Template Example

### Frontend Pull Request
```
> [#{task_id}] - {platform} - {comment/status}  
> [#{task_id}] - {platform} - {comment/status}  *if multiple bitrix card is pushed in single pull request 

Acceptance Criteria
- [ ] Criteria A
- [x] Criteria B
- [x] Criteria C

Changelog:  
- <Point 1>
- <Point 2>

Checklist Task: (optional)
- <checklist 1>
- <checklist 2>

Figma Link: <link>  

Screenshot Figma:  
<image>  
Screenshot UI: (optional)  
<image>  
Before: (optional)  
<image>  
```

**Example**
```
> [#51741] - FE Web - Done
> [#52801] - FE Web - On Progress

Acceptance Criteria
- [ ] Email format must be valid
- [x] Password and confirm password must be same
- [x] Name can not contain number

Changelog:  
- #51741 implement mock api
- #52801 Slicing and integration sidebar menu

Checklist Task: (optional)
- [FE] Menu Hadiah
- [FE] Pencarian
- [FE] Filter

Figma Link: [figma](https://www.figma.com/file/1234567/app?type=design&node-id=2200-28382&mode=design&t=Dez4oDtHUAEtdjlo-4)
```

### Backend Pull Request
```
> [#{task_id}] - {platform} - {comment/status}  
> [#{task_id}] - {platform} - {comment/status}  *if multiple bitrix card is pushed in single pull request

Acceptance Criteria
- [ ] Criteria A
- [x] Criteria B
- [x] Criteria C

Changelog:  
- <Point 1>
- <Point 2> 


Checklist Task: (optional)
- <checklist 1>
- <checklist 2>
```

**Example**
```
> [#123456] - BE - Done

Acceptance Criteria
- [x] Email must be unique
- [x] Validation password length must more than 5 chars 
- [x] Name can not contain number

Changelog:  
- CRUD master data promo API
- CRUD master data banner API
- fix upload file API
- fix migration data


Checklist Task: (optional)
- [BE] Promo
- [BE] Banner
```