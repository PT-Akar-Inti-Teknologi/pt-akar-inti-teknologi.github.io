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

## Template Example

### Frontend Pull Request
```
> [#{bitrix_task_id}] - FE Web - {comment/status}  
> [#{bitrix_task_id}] - FE CMS - {comment/status}  

Changelog:  
- <Point 1>
- <Point 2>

Bitrix Link: <link>  

Checklist Task: (optional)
- <checklist 1>
- <checklist 2>

Figma Link: <link>  

Screenshot Figma:  
<image>  
Screenshot UI:   
<image>  
Before: (optional)  
<image>  
```
### Backend Pull Request
```
> [#{bitrix_task_id}] - BE - {comment/status}  
> [#{bitrix_task_id}] - BE - {comment/status}   

Changelog:  
- Implement API A (soorfinc > mobile > API A)  
- Implement API B (soorfinc > mobile > API B)  
etc  

Bitrix Link: <link>  

Checklist Task:  
- <checklist 1>
- <checklist 2>
```