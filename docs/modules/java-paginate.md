---
layout: default
title: Pageable & Specification
permalink: /modules/java-library/pageable
parent: Java
grand_parent: Plugins & Modules
has_children: false
nav_order: 1
---

# Java Standard
{: .no_toc }

### Springboot list
  
For query list, we recommend to use pageable and java specification. Specification defines the search criteria, while Pageable dictates how the retrieved data is divided into pages

#### Pageable:
- Pageable is an interface that allows you to define pagination parameters for retrieving a subset of data from a larger result set.
- It provides methods to specify the page number, page size, sorting criteria, and more.
- By using Pageable, you can efficiently retrieve paginated data from your database.

#### Specification:
- Specification is part of the Spring Data JPA framework.
- It allows you to create dynamic queries based on specific criteria.
- You can define custom predicates (conditions) using Specification to filter data from your database.
- It’s particularly useful when you need to build complex queries with varying conditions at runtime.
  
Github: [Code Example]((https://github.com/PT-Akar-Inti-Teknologi/ait_spring_boot_template/tree/examples/search-sort-page))
  

