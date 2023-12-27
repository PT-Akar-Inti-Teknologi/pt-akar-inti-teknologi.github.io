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

### **Project Structure**

You can read more about the project structure and its explanation from the link above.

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