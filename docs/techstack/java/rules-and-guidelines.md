---
layout: default
title: Rules & Guidelines
permalink: /techstack/java/rules-and-guidelines
parent: Java
grand_parent: Techstacks Guidelines
---

# Rules & Guidelines

**If the client has a standard code, then follow that standard. But if not, then follow the rules below.**

### Project Structure

#### General Structure
```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── org.ait.project.{project-name}.{application-name}
│   │   │       └── config
│   │   │           └── exceptions
│   │   │               └── ControllerAdvisor.java
│   │   │               └── ModuleException.java
│   │   │           └── properties
│   │   │               └── part
│   │   │                   └── Part1Properties.java
│   │   │                   └── ,,,.java
│   │   │               └── ApplicationProperties.java
│   │   │           └── MessageConfig.java
│   │   │       └── modules
│   │   │           └── module1
│   │   │               └── dto
│   │   │                   └── request
│   │   │                   └── response
│   │   │                   └── ,,,.java
│   │   │               └── interfaces
│   │   │                   └── rest
│   │   │                   └── kafka (optional)
│   │   │                   └── scheduler (optional)
│   │   │               └── model
│   │   │                   └── entity
│   │   │                   └── repository
│   │   │                   └── specification
│   │   │               └── service
│   │   │                   └── core
│   │   │                       └── impl
│   │   │                       └── CoreService.java
│   │   │                   └── adapter
│   │   │                       └── query
│   │   │                           └── impl
│   │   │                               └── Module1QueryAdapterImpl.java
│   │   │                           └── Module1QueryAdapter.java
│   │   │                       └── adapter
│   │   │                           └── impl
│   │   │                               └── Module1CommandAdapterImpl.java
│   │   │                           └── Module1CommandAdapter.java
│   │   │               └── transform
│   │   │           └── moduleX
│   │   │           └── .....
│   │   │       └── shared    
│   │   │           └── constants    
│   │   │               └── enums    
│   │   │               └── statics    
│   │   │           └── dto    
│   │   │           └── feignclient    
│   │   │               └── ThirdPartyA    
│   │   │                   └── facade    
│   │   │                   └── request    
│   │   │                   └── response    
│   │   │                   └── service    
│   │   │               └── .....    
│   │   │           └── utils
│   │   │               └── Utils1.java    
│   │   │       └── Application.java
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

#### Description of substructure

##### SRC

```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── org.ait.project.{project-name}.{application-name}
│   │   │       └── config
│   │   │       └── modules
│   │   │       └── shared   
│   │   │       └── Application.java
│   │   └── resources
│   └── test
└── pom.xml

```

In general, the main project consists of 3 major packages, namely:

- **config**: This package contains configuration files that usually have the @Configuration annotation used to handle configuration when the application is running.
- **modules**: This package contains the main business components of the project.
- **shared**: This package contains classes that can be used throughout the project, such as constants, utility classes, DTOs, and etc.

### Application Properties
### Openfeign
### Liquibased

### Templates

