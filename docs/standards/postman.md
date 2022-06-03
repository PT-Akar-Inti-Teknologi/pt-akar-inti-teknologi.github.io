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

1. Root Collection, filled by platform.
  - This will make it easier for developers to focus on the platform they are working on
  - Example: CMS, Mobile, Web, etc
  
![image](https://drive.google.com/uc?export=view&id=12RIXYfbP-wZAr6XUO3Bi5P2j_IZEKf-n)
{: .text-center }

2. Inside the platform folder, create the folder based on screen/page/menu.
  - Note: because it's paged, it's natural for endpoint duplication

![image](https://drive.google.com/uc?export=view&id=1evnMTc8MXDY3w5R-iiR9Xk3kG2wO52ei)


3. Every API *MUST* have a positive case example and negative case example (Optional)

![image](https://drive.google.com/uc?export=view&id=1kZR5P8H8Uw5i9QZ1TNNBymyHQQIva0EY)

4. Each API must have an explanation in the postman documentation:
  - explanation of what this service is for
  - ENUM mapping explanation (if any). Example: for gender, M (Male) and F (Female), etc
  - explanation of the DATE format used. Example: yyyy-mm-dd, or dd-mm-yyyy, etc

![image](https://drive.google.com/uc?export=view&id=1rkjSYJpVOkpLTQjtz9YCz0J89BiyMWLD)

![image](https://drive.google.com/uc?export=view&id=1PDbonH223Enfz5utNbnwRKq-38XJU5j1)

![image](https://drive.google.com/uc?export=view&id=13Q1yztlOBHoNUTndf4oyPE21k94NNCCx)


5. in the root collection, it must have the changes log. This will make it easier for developers to understand what changes occur in each update.

![image](https://drive.google.com/uc?export=view&id=14HHgoaAzbg4ERO3pg191-53bBa9P-zAC)