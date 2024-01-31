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

Folder core berisi file-file core yang berkaitan dengan core aplikasi (tidak berkaitan dengan transaksi aplikasi)

### main.js

File entry dari project ini

### bootstrap.js

File untuk mendaftarkan router dan store pada masing-masing module

### bootstrap.js

File untuk mendaftarkan global component dan global layout yg ada di folder core/components dan core/layouts

### service.js

File untuk mendaftarkan semua file di dalam folder core/services

#### services/Api.js

- File untuk handle call API, setiap method API diimplementasi di file ini.
- Di file ini base URL dari API di daftarkan.
- Terdapat interceptor request dan response.
- Interceptor request bertujuan untuk menyisipkan token dari keycloak
- Interceptor response bertujuan untuk menghandle success message (kecuali method get) dan handle error message yang akan di lempar ke component App.vue

#### services/Component.js

Class untuk menampung global components dan global layouts dari aplikasi

#### services/Router.js

Class untuk menampung seluruh router dari semua modules (file 'router.js')

#### services/Store.js

Class untuk menampung seluruh store dari semua modules (file <module_name>.store.js)

## Modules

- Folder ini berisi semua fitur yang ada di aplikasi yang dikelompokkan kedalam beberapa module.

- Setiap module diibaratkan sebuah aplikasi kecil (terdapat page, router & store).

- Untuk contoh, bisa melihat 'module-example'.

- Untuk component dan mixin yang digunakan hanya di 1 module, bisa dibuat di dalam module tersebut (<module_name>/components & <module_name>/mixins).

- Untuk file-file lain yg digunakan untuk kepentingan module bisa menggunakan aturan yg sama seperti di atas.

- Contoh pemanggilan API bisa dilihat di module-example/store/example.store.js