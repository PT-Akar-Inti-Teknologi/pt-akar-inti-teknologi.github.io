---
layout: default
title: Rules & Guidelines
permalink: /techstack/golang/rules-and-guidelines
parent: Golang
grand_parent: Techstacks Guidelines
---

# **Rules & Guidelines**

**If the client has a standard code, then follow that standard. But if not, then follow the rules below.**

## **Golang Template Project**
[Link](https://github.com/PT-Akar-Inti-Teknologi/ait_golang_boilerplate) 
The source code can be located at the link above.

### **Project Structure**

```
|   Dockerfile
|   go.mod
|   go.sum
|   main.go
|   README.md
|   
+---cmd
|       serve_api.go
|       
+---config
|       config.yaml
|       
+---core
|   |   database.go
|   |   redis.go
|   \---helpers
|           utils.go
|           
\---internals
    +---yourmodule
    |   |   handler.go
    |   |   router.go
    |   |   
    |   +---models
    |   |       entity.go
    |   |       
    |   \---usecase
    |           yourusecase.go
    |           yourusecase_test.go
    |           
    \---yourmodule2

```

### **Description of the structure**

### internals

```
\---internals
    +---yourmodule
    |   |   handler.go
    |   |   router.go
    |   |   
    |   +---models
    |   |       entity.go
    |   |       
    |   \---usecase
    |           yourusecase.go
    |           yourusecase_test.go
    |           
    \---yourmodule2
```

`internals` contains modules/domains that is serving the purpose of this project, your models, repository, usecase and handler should be in this folder

- keep each of the module independent
- each module will serve itself

### core

```
+---core
|   |   database.go
|   |   redis.go
|   \---helpers
|           utils.go
|
```

`core` contains core function/library that will be used by our modules, for example like redis, message broker, middlewares and also helpers like utility etc that will be used by `yourmodule`

### config

```
+---config
|       config.yaml
|
```

`config` contains config related files that will be used.

### cmd
```+---cmd
|       serve_api.go
|   
```

`cmd` contains files that wrap our modules and serve it as `cli` based application. For example like `serve_api.go` that wrapping `yourmodule` as a command serve-api

### root files
```
|   Dockerfile
|   go.mod
|   go.sum
|   main.go
|   README.md
```

`main.go` works as our main function of the application

`go.mod` contains list of external libraries

`go.sum` this is auto generated files from command `go mod tidy`

`Dockerfile` here you can configure docker related commands

`README.md` Strongly suggest you write the readme file so we can know what is the application about

## **Coding Guidelines** ##

### Formatting ###

*Indentation*: Use tabs for indentation (one tab = one indentation level).

*Line Length*: Keep lines under 80 characters where feasible. If a line exceeds this, break it into multiple lines.

*Braces*: Opening braces should be on the same line as the function declaration or control structure.

### Naming Conventions ###

*Packages*: Use lowercase names for packages ex: order, payment. Avoid unnecessary abbreviation.

*Variables*: Follow camelCase for variable names. Variable names should be descriptive. ex: oldData

*Constants*: Use snake_case for constants. ex: status_order_complete

*Functions*: Follow camelCase for functions names that is unexportable. Use PascalCase for Exportable functions.

*Structs*: Use PascalCase for struct names. Exported structs should have clear and descriptive names

### Error Handling ###

*Errors*: Explicitly handle errors. Avoid suppressing them using _.

*Return Values*: Clearly define return values, especially for functions that can fail.

### Miscellaneous ###

*Concurrency*: Utilize goroutines and channels for concurrent programming.

*Error Messages*: Ensure error messages are informative and aid debugging. for ex : *myFunc() err: this is error message*

Avoid Magic Numbers and Strings: Define constants for them.

*GoLint and GoVet*: Run golint and go vet regularly to catch common issues.