---
layout: page
title: Postman
permalink: /standards/postman/
parent: Standards
has_children: false
---

# Postman
{: .no_toc }

## Why
One of the tools we will use to make the API documentation is Postman. Therefore, it is important that we have a standard for the documentation folder structure that we use to make it easier for developers to implement.

## Postman Convention

- Root Collection, filled by platform.
  - This will make it easier for developers to focus on the platform they are working on
  - Example: CMS, Mobile, Web, etc
  
![image](https://raw.githubusercontent.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/main/Postman/POINT%201.png)

- Inside the platform folder, create the folder based on screen/page/menu.
  - Note: because it's paged, it's natural for endpoint duplication

![image](https://raw.githubusercontent.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/main/Postman/POINT%202.png)


- Every API *MUST* have a positive case example and negative case example (Optional)

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Postman/POINT%203.png?raw=true)

- Each API must have an explanation in the postman documentation:
  - explanation of what this service is for
  - ENUM mapping explanation (if any). Example: for gender, M (Male) and F (Female), etc
  - explanation of the DATE format used. Example: yyyy-mm-dd, or dd-mm-yyyy, etc

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Postman/POINT%204%20-%20CONTOH.png?raw=true)

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Postman/POINT%204%20-%20A.png?raw=true)

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Postman/POINT%204%20-%20B.png?raw=true)


- in the root collection, it must have the changes log. This will make it easier for developers to understand what changes occur in each update.

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Postman/POINT%205.png?raw=true)