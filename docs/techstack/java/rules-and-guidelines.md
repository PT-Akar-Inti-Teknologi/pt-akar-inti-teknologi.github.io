---
layout: default
title: Rules & Guidelines
permalink: /techstack/java/rules-and-guidelines
parent: Java
grand_parent: Techstacks Guidelines
---

# **Rules & Guidelines**

**If the client has a standard code, then follow that standard. But if not, then follow the rules below.**

## **Java Template Project**

[Link](https://github.com/PT-Akar-Inti-Teknologi/ait-spring-boot-template)

## **Guidelines**
### **Project Structure**

#### **General Structure**
```

├── src
│   ├── main
│   │   ├── java
│   │   │   ├── org.ait.project.{project-name}.{application-name}
│   │   │   │    ├── config
│   │   │   │    │    ├── exceptions
│   │   │   │    │    │    ├── ControllerAdvisor.java
│   │   │   │    │    │    └── ModuleException.java
│   │   │   │    │    ├── properties
│   │   │   │    │    │    ├── part
│   │   │   │    │    │    │    ├── Part1Properties.java
│   │   │   │    │    │    │    └── ,,,.java
│   │   │   │    │    │    └── ApplicationProperties.java
│   │   │   │    │    └── MessageConfig.java
│   │   │   │    ├── modules
│   │   │   │    │    ├── module1
│   │   │   │    │    │    ├── dto
│   │   │   │    │    │    │    ├── request
│   │   │   │    │    │    │    ├── response
│   │   │   │    │    │    │    └── ,,,.java
│   │   │   │    │    │    ├── interfaces
│   │   │   │    │    │    │    ├── rest
│   │   │   │    │    │    │    ├── kafka (optional)
│   │   │   │    │    │    │    └── scheduler (optional)
│   │   │   │    │    │    ├── model
│   │   │   │    │    │    │    ├── entity
│   │   │   │    │    │    │    ├── repository
│   │   │   │    │    │    │    └── specification
│   │   │   │    │    │    ├── service
│   │   │   │    │    │    │    ├── core
│   │   │   │    │    │    │    │    ├── impl
│   │   │   │    │    │    │    │    └── CoreService.java
│   │   │   │    │    │    │    └── adapter
│   │   │   │    │    │    │        └── query
│   │   │   │    │    │    │            └── impl
│   │   │   │    │    │    │                └── Module1QueryAdapterImpl.java
│   │   │   │    │    │    │            └── Module1QueryAdapter.java
│   │   │   │    │    │    │        └── adapter
│   │   │   │    │    │    │            └── impl
│   │   │   │    │    │    │                └── Module1CommandAdapterImpl.java
│   │   │   │    │    │    │            └── Module1CommandAdapter.java
│   │   │   │    │    │    └── transform
│   │   │   │    │    ├── moduleX
│   │   │   │    │    └── .....
│   │   │   │    ├── shared    
│   │   │   │    │    ├── constants    
│   │   │   │    │    │    ├── enums    
│   │   │   │    │    │    └── statics    
│   │   │   │    │    ├── dto    
│   │   │   │    │    ├── feignclient    
│   │   │   │    │    │    ├── ThirdPartyA    
│   │   │   │    │    │    │    ├── facade    
│   │   │   │    │    │    │    ├── dto    
│   │   │   │    │    │    │    │    └── request    
│   │   │   │    │    │    │    │    └── response   
│   │   │   │    │    │    │    ├── service    
│   │   │   │    │    │    └── .....    
│   │   │   │    │    └── utils
│   │   │   │    │        └── Utils1.java    
│   │   │   │    └── Application.java
│   │   └── resources
│   │       └── db.changelog
│   │       └── messages
│   │           └── core
│   │           └── validation
│   │       └── application.yaml
│   │       └── application-profile1.yaml
│   │       └── application-profile2.yaml
│   └── test
└── pom.xml

```

#### **Description of substructure**

##### **SRC**

```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── org.ait.project.{project-name}.{application-name}
│   │   │       ├── config
│   │   │       ├── modules
│   │   │       ├── shared   
│   │   │       └── Application.java
│   │   └── resources
│   └── test
└── pom.xml

```

In general, the main project consists of 3 major packages, namely:

- **config**: This package contains configuration files that usually have the @Configuration annotation used to handle configuration when the application is running.
- **modules**: This package contains the main business components of the project.
- **shared**: This package contains classes that can be used throughout the project, such as constants, utility classes, DTOs, and etc.

##### **CONFIG**

```
├── config
│    ├── exceptions
│    │    ├── ControllerAdvisor.java
│    │    └── ModuleException.java
│    ├── properties
│    │    ├── part
│    │    │    ├── Part1Properties.java
│    │    │    └── ,,,.java
│    │    └── ApplicationProperties.java
│    └── MessageConfig.java
```

Based on the previous explanation, the "config" package contains configuration files used in the project.

In addition, there are several default packages that should exist in the project, including:

- **Exception**: Contains the ControllerAdvisor class (a class used to capture exceptions when processing Rest API) and the ModuleException class (a default class used in the project as the parent class that will be extended in the exception class inside the module to return the result from the Rest API).

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/controlleradvisor.png?raw=true)
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/moduleexception.png?raw=true)

- **Properties**: Contains the ApplicationProperties class which will be used as a bridge between the values in the application.yml file and the application. This part also includes partitions of property values, so each partition has a different configuration prefix.

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/properties1.png?raw=true)
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/properties2.png?raw=true)

- **MessageConfig.java**: A built-in class used to handle translating messages that are located in resources/messages/core.

###### **Notes**
**Not all values in the application.yml file are included in the class ApplicationProperties.java, only the values that are used.**

##### **Modules**

```
├── modules
│    ├── module1
│    │    ├── dto
│    │    │    ├── request
│    │    │    ├── response
│    │    │    └── ,,,.java
│    │    ├── interfaces
│    │    │    ├── rest
│    │    │    ├── kafka (optional)
│    │    │    └── scheduler (optional)
│    │    ├── model
│    │    │    ├── entity
│    │    │    ├── repository
│    │    │    └── specification
│    │    ├── service
│    │    │    ├── core
│    │    │    │    ├── impl
│    │    │    │    └── CoreService.java
│    │    │    └── adapter
│    │    │        └── query
│    │    │            └── impl
│    │    │                └── Module1QueryAdapterImpl.java
│    │    │            └── Module1QueryAdapter.java
│    │    │        └── adapter
│    │    │            └── impl
│    │    │                └── Module1CommandAdapterImpl.java
│    │    │            └── Module1CommandAdapter.java
│    │    └── transform
│    ├── moduleX
│    └── .....

```

The module package is a package that contains the main modules of a project that will be worked on. Inside each module, there is a specific structure that needs to be followed, including:

- dto: This package contains the DTO files that are only used within the module.
- interfaces: This package contains triggers in the form of REST APIs, schedulers, or other triggers such as Kafka listeners, etc., that are implemented by the module.
- model: This package contains entities, repositories, and specifications that are specific to communicating with the database.
- service:
  - core: The core package contains service classes that handle the business logic in the application.
  - adapter: This package contains classes that interact with the database.
    - query: This package contains classes that are **only allowed to read data** from the database.
    - command: This package contains classes that **process data** in the database.
- transform: This package contains MapStruct mapper interfaces that are **only used** within the related module.

###### **Notes**

1. **Each module is isolated from other modules**. To communicate or access data from a different module, use Adapters (whether it's a Query or Command) and call their interfaces.
2. **To avoid Circular Dependencies**, the Query adapter and Command adapter **should not call each other**.
3. To create a new object, you can utilize the Factory Pattern by leveraging the **MapStruct library**.

   ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/mapstruct.png?raw=true)
4. **MapStruct mappers should only be used within the core service**. If you need to use them in other modules, it is recommended to **move** the mappers to the "shared" package.
5. If there are multiple database connections within a module, you can create a new package inside the model package based on the connected database.

   ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/multipledataresource.png?raw=true)
##### **Shared**

```
├── shared    
│    ├── constants    
│    │    ├── enums    
│    │    └── statics    
│    ├── dto    
│    ├── feignclient    
│    │    ├── ThirdPartyA    
│    │    │    ├── facade    
│    │    │    ├── dto    
│    │    │    │   └── request    
│    │    │    │   └── response   
│    │    │    ├── service    
│    │    └── .....    
│    └── utils
│        └── Utils1.java
```

Based on the provided information, it seems like the "shared" package contains classes that are used throughout the project. It is similar to a configuration package, but it contains logic and constant values that are used across the project.

## Rules

### Openfeign

To use openfeign, the following package structure is required.

```
├── feignclient    
│    ├── ThirdPartyA    
│    │    ├── facade    
│    │    ├── dto    
│    │          └── request    
│    │          └── response    
│    │    ├── service 
```

- For every third-party, create a package that contains facade, request, response, and service.
  - **facade**: contains the Feign interface that will be used to make calls to the third-party API and includes a fallback class to handle failures in API calls.
  - **request and response** :  packages contain DTO classes used in the API call process.
  - **service** : package contains classes that call the Feign interface in the facade and process the data in those classes.

example:
1. ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/feign1.png?raw=true)
2. ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/feign2.png?raw=true)
3. ![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/feign3.png?raw=true)

### Liquibased

To use liquibase, the following structure can be used.

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/Java/liquibasestructure.png?raw=true)

The following files are available:

1. **schema**: it is a file that contains the database structure.
2. **seeder**: it fills the initial data when the application is run.
3. **seederdata**: it is the source of initial data used by the seeder during application runtime, usually in file format such as CSV.

The following are the specific naming conventions for schema and seed that must be followed.

**Schema**:

`
changelog-{sequience}-{action}.yml
`

**example**:

`
changelog-00001-InitTable.yml
`

**Seeder**:

`
seeder-{sequience}-{action}.sql
`

**example**:

`
seeder-00001-InitTable.sql
`

### Testcontainer

COMING SOON