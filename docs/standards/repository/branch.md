---
layout: default
title: Branch Name
permalink: /standards/repository/branch
parent: Code Repository
grand_parent: Standards
nav_order: 4
---

# Branch Name

## Why

Git offers flexible branching strategies which is really useful for collaboration and CI/CD automation. However, not using appropriate naming conventions leads to confusion and complicates the code maintenance.

## Convention

Generally, there are two kinds of branches: Regular & Temporary Branches.

### Regular Git Branches

These branches will be available permanently in a repository.

- `main` is the main branch and used for production. It should be stable all the time and no direct commits are allowed. Changes in this branch should be done **ONLY** by merging from other regular branch such as `staging`.

- `staging` contains all the code for QA, user testing or automation testing of all changes implemented. Before any change goes to production environment, it must go through this branch.

- `development` is the main **development** branch. This is where all developers contribute to project by commiting changes directly or using Pull Request (PR). The later is more preferable.

Optionally, there may be additional Git branches that need to be kept permanently in a repository. For example, to mark a certain milestone (e.g: sprints) or different environments or architecture (e.g: OS versions). Some conventions that need to be followed are:

- make it as short as possible: `ubuntu20` instead of `for_server_with_ubuntu_version_20`
- use underscore as separator: `multi_module` not `multi module`
- ask yourself whether it is necessary to keep it permanently in the repository, otherwise use temporary git branch

### Temporary Git Branches

As the name indicates, these are branches that can be created and deleted when needed. For naming use the following format,

```
group/card-description
```

`group` is used to group the branch by its purpose, which can be as follows:

- `bugfix` for Bug Fix Branches: contains fixes for known bugs or QA findings
- `hotfix` for Hot Fix Branches: contains urgent fixes, usually small changes and immediate to fix a problem in production, hence the urgency
- `feat` for Feature Branches: new features that eventually be merged into regular branch
- `experiment` for Experimental Branches: contains experimental code with new library, architecture, tools etc that need to be shared with others
- `wip` for WIP (Work In Progress) Branches: contains works that won't be finished soon or need to be completed by other

`card`
- If related JIRA cards exist, include them in the card section
- For multiple JIRA cards, separate them with a underscore (_)
- example: feat/DEMO-1234_DEMO-4567-login

`description` describes the branch using the following conventions:

- use all lower case: `bugfix/login` not `BugFix/Login`
- make it as short as possible: `feat/operational_hours` instead of `feat/implementing_store_operational_hours`
- use noun: `feat/ldap_integration` instead of `feat/integrates_ldap`
- use underscore as separator: `wip/payment_gateway` not `wip/payment-gateway`
