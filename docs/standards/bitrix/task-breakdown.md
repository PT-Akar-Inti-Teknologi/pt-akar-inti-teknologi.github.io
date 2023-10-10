---
layout: default
title: Bitrix Task Breakdown
permalink: /standards/bitrix/task-breakdown
parent: Bitrix
grand_parent: Standards
nav_order: 1
---

# Bitrix Task Breakdown
{: .no_toc }

## Items that should be included in the Technical Breakdown:

- Data: Information including data type and data length.
- Validation: Any validations that need to be considered and must be explained.
- (Optional, only for complex features) Detailed flow in the form of an activity diagram and its explanation.
- (Optional, only for complex features) Screen flow

## Used Tools

- PlantUML: https://plantuml.com/
  
  - save generated uml in one of the git repositories.



## Example

**Feature Screening Data**

- Data
  - Screen Input: 
    - Mobile Id: Input 
      - Type: alphanumeric 
      - Length: 10 
      - FE Validation: mandatory, must be filled
    - App Id: Input 
      - Type: alphanumeric 
      - Length: 10 
  - Screen Detail: 
    - NIK: Output obtained from the dukcapil API
      - Type: numeric 
      - Length: 16 
    - Nama: Output obtained from the dukcapil API
      - Type: alphanumeric 
      - Length: 50 
  - etc
- Validation
  - MID Length Validation (UI validation)
  - APPID Length Validation (UI validation)
  - APPID / MID not found
  - APPID / MID Customer Deceased
- Detail Flow
  
  ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Bitrix/Breakdown/1.png?raw=true)

  - User Input MID or APP ID
  - Then hit the API provided by BCAF
  - If not found, return a failed alert and data not found
  - If found, validate the data by hitting the Dukcapil API
  - If the consumer is deceased, add the deceased status to the data
  - Then save the data and return it to be displayed on the screen
- Screen flow 

  ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Bitrix/Breakdown/1.png?raw=true)

