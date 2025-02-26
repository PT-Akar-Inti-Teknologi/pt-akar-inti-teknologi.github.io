---
layout: default
title: Repository Name
permalink: /standards/repository/name
parent: Code Repository
grand_parent: Standards
nav_order: 1
---

# Repository Name

## Why

From time to time, developers refer to an old project as a reference when working on a new and similar one, hence repositories should be easy to search by its name, clear and self-explanatory.

## Convention

- It should be all in lowercase
- It should be in snake case, using underscore (`_`). Correct: `ait_jira`. Wrong: `AIT-jira`
- The second part should be the known code name of the project. For example `ait-web` for AIT Website,  this should be in sync with the client code in CRM used by other departments.
- The next part should be the domain specific part of the project. For example `backend` for Backend part, `frontend` for web application part, `mobile` for mobile app developed using hybrid framework such as Flutter or React Native, `android` and `ios` each for mobile app developed in native.
- For microservice module, you should include the module name in the repository name. For example, in the JHD project, you have two modules, authentication and product, so the repository names should be `jhd_web_authentication_backend` and `jhd_web_product_backend`.
