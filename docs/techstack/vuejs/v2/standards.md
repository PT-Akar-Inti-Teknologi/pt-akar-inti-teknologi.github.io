---
layout: default
title: VueJS Standards
permalink: /techstack/vuejs/v2/standard
parent: VueJS
grand_parent: Techstacks Guidelines
---

# Java Standard

## Tools Requirement

### Code Editor
we will be using **Visual Studio Code** as our Code Editor for work. [link](https://code.visualstudio.com/)

### NodeJS Version
- As a standard, we will be using **NodeJS 14** to create new projects.

### Standard plug-in
- ESLint [Link](https://eslint.vuejs.org/)
- Prettier [Link](https://www.npmjs.com/package/eslint-plugin-prettier-vue)
- Vetur [Link](https://vuejs.github.io/vetur/)

### CSS Framework

#### Tailwind (Recommended)
- Pure Tailwind
- Daisy UI
- Vue Tailwind

#### Bootstrap
- Bootstrap Vue

### Other Library
| Router | vue-router |
| State Management | vuex*, pinia* |
| Http Client | axios, fetch |
| Validation | vee-validate |
| Micro Frontend | single-spa-vue |
| Unit Test | jest |
| Datetime | date-fns, day-js |
| Utility | lodash, ramda |

### Project Structure

- Root directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-root.png?raw=true)

- Src directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-src.png?raw=true)

#### Explanation
- assets (contains images, css, files)​
- components (contains global component)​
- constants (contains constants static variable)​
- layouts (contains global layout)​
- plugins (contains external / 3rd party library)​
- services (contains global setup api, component, router, and store)

- Core directory
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/str-core.png?raw=true)

#### Explanation
- pages (contains all pages inside modules)
- router (contains registered route in modules)​
- store (contains state management files)

### Style Guide

#### Component Name
Using slug-case or PascalCase
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-name.png?raw=true)

#### Component Files​
Each component should be in its own file​
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-files.png?raw=true)

#### Base Component Names
Correct component naming
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-naming-component-file.png?raw=true)

#### Tightly Coupled Component Names​
Combining component names
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-combining.png?raw=true)

#### Self-closing Components​
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-implement.png?raw=true)

#### Prop Definitions​
Prop definitions should be as detailed as possible​
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-prop.png?raw=true)

#### Prop Name Casing​
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-prop-naming.png?raw=true)

#### Component Style Scoping​
Except global component, the other components should always be scoped​
![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Techstack/VueJS/V2/sg-component-style-scopped.png?raw=true)