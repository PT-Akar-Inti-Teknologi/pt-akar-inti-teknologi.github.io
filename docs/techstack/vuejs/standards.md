---
layout: default
title: VueJS Standards
permalink: /techstack/vuejs/standard
parent: VueJS
grand_parent: Techstacks Guidelines
---

# VueJS Standard

## Tools Requirement

### Code Editor
we will be using **Visual Studio Code** as our Code Editor for work. [link](https://code.visualstudio.com/)

### NodeJS Version
- As a standard, we will be using **NodeJS 18** or Above to create new projects Vue 3.
- And also, we will be using **NodeJS 14** or Above to develop existing project using Vue 2.
- You can download the latest version of NodeJS from [here](https://nodejs.org/en/download/)

### Standard plug-in
- [ESLint](https://eslint.vuejs.org/)
- [Prettier](https://www.npmjs.com/package/eslint-plugin-prettier-vue)
- [Vetur](https://vuejs.github.io/vetur/)
- [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

### CSS Framework

#### Tailwind (Recommended)
- Pure Tailwind
- Daisy UI
- Vue Tailwind

#### Bootstrap
- Bootstrap Vue

#### Default Setup Project
- Vue 2
  - Javascript
  - Option API
- Vue 3
  - Typescript
  - Composition API

*(Note) : The migration project from Vue 2 is given the convenience of continuing to use JavaScript and Option API setup​*

### Other Library

| Category          | Library          |
|-------------------|------------------|
| Router            | vue-router       |
| State Management  | vuex^, pinia^^   |
| Http Client       | axios, fetch     |
| Validation        | vee-validate     |
| Micro Frontend    | single-spa-vue   |
| Unit Test         | jest             |
| Datetime          | date-fns, day-js |
| Utility           | lodash, ramda    |

*Note : (^)Vue2 (^^)Vue3*

### Project Structure Vue 2

#### Explanation Core directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-core.png?raw=true)

- assets (contains images, css, files)​
- components (contains global component)​
- constants (contains constants static variable)​
- layouts (contains global layout)​
- plugins (contains external / 3rd party library)​
- services (contains global setup api, component, router, and store)

#### Explanation Modules directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-src.png?raw=true)

- pages (contains all pages inside modules)
- router (contains registered route in modules)​
- store (contains state management files)

### Project Structure Vue 3

#### Explanation Core directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-core-vue3.png?raw=true)

- assets (contains images, css, files)​
- components (contains global component)​
- interfaces (contains list of interface)​
- layouts (contains global layout)​
- plugins (contains external / 3rd party library)​
- services (contains global setup api, component, router, and store)

#### Explanation Modules directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-src-vue3.png?raw=true)

- components (contains all components in modules)
- interfaces (contains all interfaces inside in modules)
- pages (contains all pages inside modules)
- router (contains registered route in modules)​
- store (contains state management files)

### Style Guide

**1. Component Name**

***Vue 2*** Using slug-case or PascalCase

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-name.png?raw=true)

***Vue 3*** Using setup script

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-name-vue3.png?raw=true)

**2. Component Files​**

Each component should be in its own file​

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-files.png?raw=true)

**3. Base Component Names**

Correct component naming

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-naming-component-file.png?raw=true)

**4. Tightly Coupled Component Names​**

Combining component names

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-combining.png?raw=true)

**5. Self-closing Components​**

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-implement.png?raw=true)

**6. Prop Definitions​**

Prop definitions should be as detailed as possible​

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-prop.png?raw=true)

**7. Prop Name Casing​**

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-prop-naming.png?raw=true)

**8. Component Style Scoping**

Except for global components, the other components should always be scoped.

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-style-scopped.png?raw=true)
