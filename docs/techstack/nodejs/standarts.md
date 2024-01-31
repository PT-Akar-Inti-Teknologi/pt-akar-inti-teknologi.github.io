---
layout: default
title: NodeJs Standarts
permalink: /techstack/nodejs/standarts
parent: NodeJs
grand_parent: Techstacks Guidelines
---

# NodeJs Standard

## Main Requirement

### IDE
Preferable to use [Microsoft Visual Studio Code](https://code.visualstudio.com/Download) as majority for IDE preferences.

### Standard Plug-ins
To improve our Quality of Code, we need to mandatory install of following extensions OR plugins:
- [SonarLint](https://docs.sonarsource.com/sonarlint/vs-code/getting-started/installation/)
- [ESLint](https://eslint.org/docs/latest/use/getting-started)
- [Prettier](https://prettier.io/docs/en/install)
- [GitLens](https://gitlens.amod.io/), or any prefereable git tool / client

### Frameworks
For framework we use **[NestJS](https://nestjs.com/)** as our main framework.

> NOTE: this may vary depending each project, at the moment for majority projects still use NestJS v9.x.x

### NodeJS Version
As for standard we currently use stable LTS version, and depends on what NestJS minimum requirement for Node version.

### Dependencies
| Dependencies | NPM Package Name |
|--|--|
| Http Client | @nestjs/axios |
| JWT | @nestjs/jwt |
| Authentication | @nestjs/passport, @nestjs/passport-jwt |
| Database / ORM | TypeOrm, @nestjs/typeorm |
| Validator | class-validator, class-transformer |
| Logger | @nestjs / Winston / Fluentd |
