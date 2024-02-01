---
layout: default
title: NodeJs Rules & Guidelines
permalink: /techstack/nodejs/rules-and-guidelines
parent: NodeJs
grand_parent: Techstacks Guidelines
---

# Rules and Guideline

> NOTE: if the client has a standard code, then follow that standard. But if not, then follow the rules below Blockquote

## NodeJs Template Project
GitHub Repo: [building_block_admin](https://github.com/PT-Akar-Inti-Teknologi/building_blocks_admin_backend)

## Formatting
*indentation*: use indentation with `space` with value `2`.
*quotation*: preferable to use use single quote (`'`).

## Naming Convention
#### General Rule
- Always use Camel Case naming for general usage (eg. class, method, function, variable).
- For database table name use Snake Case with underscore (`_`) (eg. `auth_user`, `auth_otp`).

#### DTO
- Naming class context should use Camel Case.
- Last suffix should use `DTO` with upper cased.
- Representation of context should be clear; use (`Create`, `Update`, `Get`, `List`, etc.)
- example: `CreateUserDTO`, `GetUserDTO`, `UpdateUserDTO`

#### Controllers
- Controller naming class should use Camel Case.
- Controller URL should separated with dash (`-`)
- Last suffix should use `Controller`.
- Representation of `@Controller()` should use name of the controller context.

example:
```
class DailyIncomeController
```
should have decorator

` @Controller('daily-incomes')`

it should became
```
...
@Controller('daily-incomes')
class DailyIncomeController() {
...
```

#### Entity / Schema
- Entity naming class should use Camel Case.
- Suffix should ended with `Document`.
- Joined table in entity should use Snake Case.
- Entity should **NOT** contain any logic business.
- Table should be normalized.

example

```
@Entity({ name: 'user' })
export class UserDocument {
...
}
```

#### Interface
- interface naming should use Camel Case.
- interface should always started with prefix `I`, (eg. `IUserService`, `IUserRepository`) .

#### Services
- Service naming class should use Camel Case.
- Service should ended with suffix `Service`.
- Make sure returned type from service not contain `response_output`, from `ResponseService` class.

## Do and Don't (s)

- TypeoOrm: Where
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-typeorm-where.png)

- Variable Naming
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-variable-naming.png)

- Wrap in Promise.all()
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-wrap-promise.png)

- Saving Data
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-saving-data.png)

- Response Type
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-response-type.png)

- Parameter Naming
![image](https://github.com/PT-Akar-Inti-Teknologi/pt-akar-inti-teknologi.github.io/blob/docs/nodejs-standard/docs/techstack/nodejs/images/dnd-parameter-naming.png)