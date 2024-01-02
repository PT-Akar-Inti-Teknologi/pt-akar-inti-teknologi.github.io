---
layout: default
title: Golang Standards
permalink: /techstack/golang/standard
parent: Golang
grand_parent: Techstacks Guidelines
---

# Golang Standard

## Main Requirement

### IDE
We can use Visual Studio Code [link](https://code.visualstudio.com/) or even better Goland (not free) [link](https://www.jetbrains.com/go/) for our IDE

#### standard plug-in
- Go [Link](https://marketplace.visualstudio.com/items?itemName=golang.go)

### Framework

we prefer native Go because it have no dependencies, but not limited to other framework like **Gin** or **Fiber**. 

### Go Version

As a standard, we will be using **go 1.18** but not limited to other newer *stable* releases.

### Recommended External Libraries 

### Chi
This library act as our Go Http services. You can learn more [here](https://go-chi.io/)

### Urfave/cli
This library helps us to wrap/write our code as cli based application. You can learn more [here](https://cli.urfave.org/)

### Testify
This library helps us writing unit test, like mocking database or restful. You can learn more [here](https://pkg.go.dev/github.com/stretchr/testify)

### Viper
This library helps us configure config files management with support for various formats (YAML, JSON, TOML). You can learn more [here](https://github.com/spf13/viper)

### Gorm
This library act as our ORM library for Go that supports MySQL, PostgreSQL, SQLite, etc. You can learn more [here](https://gorm.io/index.html)