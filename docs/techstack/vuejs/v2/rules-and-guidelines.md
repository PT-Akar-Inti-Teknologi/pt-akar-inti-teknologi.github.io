---
layout: default
title: Rules & Guidelines
permalink: /techstack/vuejs/v2/rules-and-guidelines
parent: VueJS
grand_parent: Techstacks Guidelines
---

# **Rules & Guidelines**

**If the client has a standard code, then follow that standard. But if not, then follow the rules below.**

## **VueJS Template Project**

[Link](https://github.com/PT-Akar-Inti-Teknologi/bca_dlog_newbi_template)

## **Guidelines**
### **Project Structure**

#### **General Structure**
```
.
├── public/
│   ├── favicon.ico
│   └── index.html
├── src/
│   └── core/
│       ├── assets/
│       │   └── theme.css
│       ├── components/
│       │   └── ExampleComponent.vue
│       ├── layouts/
│       │   └── ExampleLayout.vue
│       ├── plugins/
│       │   └── sentry/
│       │       └── index.js
│       ├── services/
│       │   ├── Api.js
│       │   ├── Component.js
│       │   ├── Router.js
│       │   └── Store.js
│       ├── App.vue
│       ├── bootstrap.js
│       ├── componentRegister.js
│       ├── main.js
│       ├── service.js
│       └── set-public-path.js
├── modules/
│   └── module-example/
│       ├── pages/
│       │   └── Example.vue
│       ├── router/
│       │   └── router.js
│       └── store/
│           └── example.store.js
├── .browserslistrc
├── .env.standalone
├── .eslintrc.js
├── .gitignore
├── README.md
├── babel.config.js
├── jest.config.js
├── package-lock.json
├── package.json
└── vue.config.js

```

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your unit tests

```
npm run test:unit
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# Notes

## Core

The core folder contains core-related files that are not related to application transactions.

### main.j

The entry file of this project.

### bootstrap.js

File for registering routers and stores in each module.

### service.js

File for registering all files in the core/services folder.

#### services/Api.js

- File for handling API calls; each API method is implemented in this file.
- In this file, the base URL of the API is registered.
- There are request and response interceptors.
- The request interceptor aims to insert the token from Keycloak.
- The response interceptor aims to handle success messages (except for the GET method) and handle error messages that will be thrown to the App.vue component.

#### services/Component.js

Class to hold global components and global layouts for the application.

#### services/Router.js

Class to hold all routers from all modules (file 'router.js').

#### services/Store.js

Class to hold all stores from all modules (file <module_name>.store.js).

## Modules

- This folder contains all the features of the application grouped into several modules.
- Each module is considered a small application (with pages, routers, and stores).
- For example, you can refer to 'module-example'.
- For components and mixins used only in one module, they can be created within that module (<module_name>/components & <module_name>/mixins).
- For other files used for module purposes, the same rules as above can be applied.
- An example of API invocation can be seen in module-example/store/example.store.js.