---
layout: default
title: Java Standards
permalink: /techstack/java/standard
parent: Java
grand_parent: Techstacks Guidelines
---

# Java Standard

## Main Requirement

### IDE
we will be using **IntelliJ IDEA** as our IDE for work. [link](https://www.jetbrains.com/idea/)

#### standard plug-in
- SonarLint [Link](https://plugins.jetbrains.com/plugin/7973-sonarlint)
- Checkstyle-IDEA [Link](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea)
- Codeium-AI [Link](https://plugins.jetbrains.com/plugin/20540-codeium-ai-autocomplete-and-chat-for-python-js-ts-java-go-)
- Endpoints Explorer [Link](https://plugins.jetbrains.com/plugin/17867-endpoints-explorer)
- RoboPOJOGeneratpr [Link](https://plugins.jetbrains.com/plugin/8634-robopojogenerator)

### Framework

we use **Spring Boot** as our main framework & **Maven** as our compiler.

We will be using **Spring Boot version 3**.

### Java Version

As a standard, we will be using **Java 17** to create new projects.

### Note

The version of **Spring Boot and Java used will depend on the client's requirements**.
**If there are no specific** requirements from the client, we will use the standard mentioned above to create a new project.

## Dependencies
### Openfeign

A Java framework used to easily and elegantly create HTTP clients. This framework is used to communicate with web services or APIs from Java applications. OpenFeign integrates with Spring Cloud, making it commonly used in microservice applications built with Spring Boot.

[reference](https://spring.io/projects/spring-cloud-openfeign)

### Liquibase

Liquibase is a tool used in software development and database management. This tool allows developers and database administrators to manage the structure of the database schema in a structured, documented, and secure way. Liquibase is used to manage changes to the database schema, such as creating new tables, modifying columns, deleting indexes, and more, using an approach called 'Database Refactoring'.

[reference](https://www.baeldung.com/liquibase-refactor-schema-of-java-app)

### Mapstruct

MapStruct is an object mapping framework used in Java application development. The main purpose of MapStruct is to automatically generate object mapping code, allowing developers to easily transform data from one object to another without having to write manual mapping code. MapStruct can be used in various contexts, including microservices-based applications, data processing, and Spring-based applications.

[reference](https://mayankposts.medium.com/simplify-model-mapping-in-spring-boot-with-mapstruct-and-lombok-65d93b56a76b)

### Lombok

MapStruct is an object mapping framework used in Java application development. The main purpose of MapStruct is to automatically generate object mapping code, allowing developers to easily transform data from one object to another without having to write manual mapping code. MapStruct can be used in various contexts, including microservices-based applications, data processing, and Spring-based applications.

[reference](https://www.baeldung.com/intro-to-project-lombok)

### Zalando Logbook

Apache HttpClient is a Java library that can be extended to enable comprehensive logging of requests and responses for various client and server-side technologies. It fulfills specific needs by allowing web application developers to log any HTTP traffic received or sent by the application in a way that makes it easy to store and analyze it later. This can be useful for traditional log analysis, meeting audit requirements, or investigating individual historical traffic issues.

[reference](https://github.com/zalando/logbook)

### Test Containter

TestContainer is a tool that helps us run integration tests on our code.

[reference](https://testcontainers.com/guides/testing-spring-boot-rest-api-using-testcontainers/)

### Envers (Optional)

Hibernate Envers is a project used for auditing or historical recording of entities (objects) in applications that use Hibernate as an Object-Relational Mapping (ORM) framework. With Hibernate Envers, you can automatically track data changes on entities, including who made the changes, when the changes occurred, and what the changes were.

[reference](https://www.baeldung.com/database-auditing-jpa)