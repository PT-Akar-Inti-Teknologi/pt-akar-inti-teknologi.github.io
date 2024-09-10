---
layout: default
title: Bitrix Checklist
permalink: /standards/bitrix/checklist
parent: Bitrix
grand_parent: Standards
nav_order: 2
---

# Bitrix Checklist
{: .no_toc }

## Why
Having a common bitrix standard is crucial as it simplifies the work for everyone involved.

## How to Create a Checklist

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Bitrix/Checklist/1.jpg?raw=true)

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Bitrix/Checklist/2.png?raw=true)

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Bitrix/Checklist/3.png?raw=true)

## Checklist Requirements

### Template

[{platform}] {to do task} [{Mandays}] {assign dev} [start: {start-date}, est: {est}]  [Done at: {done-at}] 

### Description
- Platform: BE / FE 

- To do task: Describe the task performed by the developer

- Mandays: Specify the duration of the task

- Assign dev: Identify the developer assigned to the task

- Start-date: Mention the date when the task started

- Est: Provide an estimated completion date

- Done-at: Specify the date when the task was completed


And some optional items depending on conditions

- Blocker at: Add this when the task cannot be completed due to blockers

- Start again: Add this in the format [start: {start-date}, est: {est}] to indicate resuming work after resolving blockers

## Example

### Gathering Phase

After technical breakdown

[BE] Implement API Feature A [xMD]

After Estimating Mandays

[BE] Implement API Feature A [5MD]

```
### Development Phase
```

### When assigned to a developer

[BE] Implement API Feature A [5MD] Sukirman [Start: 10-08-2023, est: 15-08-2023]

### Upon completion

~~[BE] Implement API Feature A [5MD] Sukirman [Start: 10-08-2023, est: 15-08-2023] [done at: 13-08-2023]~~

**Checklist completed**

### When a blocker occurs

[BE] Implement API Feature A [5MD] Sukirman [Start: 10-08-2023, est: 15-08-2023] [Blocker at: 12-08-2023]

Include information about the blocker and the reason for it

### When the blocker is solved and work resumes

[BE] Implement API Feature A [5MD] Sukirman [Start: 10-08-2023, est: 15-08-2023] [Blocker at: 12-08-2023] [start again: 14-08-2023, est: 17-08-2023]
