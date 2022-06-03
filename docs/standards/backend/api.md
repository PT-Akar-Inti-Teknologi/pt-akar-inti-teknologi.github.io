---
layout: default
title: API Convention
permalink: /standards/backend/api-convention
parent: Backend
grand_parent: Standards
nav_order: 1
---

# API Convention

## Why

In order to provide consistent developer experience across many APIs and over a long period of time, all names used by an API should be:

- simple
- intuitive
- consistent

## Common Conventions
- All resource names should use nouns in plural form. 
- For names that have more than one word on it, use hyphens (-) to preserve the url readability. Try to avoid using underscores ( _ ) for endpoint’s url at all cost. Example:
  - http://api.example.com/inventory-management/managed-entities/{id}/install-script-location
- Do not use underscores (_).
- Use lowercase letters in every URI representation.
- Use nouns and no verbs to represent resources. Example:
  - http://api.example.com/device-management/managed-devices 
  - http://api.example.com/device-management/managed-devices/{device-id}
  - http://api.example.com/user-management/users/ 
  - http://api.example.com/user-management/users/{id} 
- Use query parameters (in bold) to apply filters on resources. For query names containing more than one word, use underscores ( _ ) as delimiter. Example:
  - http://api.example.com/device-managements/managed-devices?**region_area=USA&brand=XYZ&sort=installation-date**

## Endpoint Naming Principles

Try separating API by logical resources (hint: usually things written as nouns) names such as 'users', 'coupons', 'transactions', or 'movies'. Once resources are defined, identify what actions can be applied to it. Map those actions using HTTP methods available. 

There are at least three common cases we found when naming an endpoint:

### 1. Common CRUD

For common CRUD API actions, follow the usual. Example: a ‘ticket’ resource could have CRUD actions mapped to HTTP methods like these:

- GET /tickets - Retrieves a list of tickets
- GET /tickets/12 - Retrieves a specific ticket with id of 12 
- POST /tickets - Creates a new ticket
- PUT /tickets/12 - Updates ticket #12
- DELETE /tickets/12 - Deletes ticket #12 

### 2. Resources relations

If a resource is related to another resource, and the relation can only exist within that resource, then logically map those resources to the parent resource. Example between 'posts' and 'comments':

- GET /posts/12/comments - Retrieves list of comments for posts #12
- GET /posts/12/comments/5 - Retrieves comments #5 for posts #12
- POST /posts/12/comments - Creates a new comments in posts #12
- PUT /posts/12/comments/5 - Updates comments #5 for posts #12
- PATCH /posts/12/comments/5 - Partially updates comments #5 for posts #12
- DELETE /posts/12/comments/5 - Deletes comments #5 for posts #12

### 3. Actions not fitting in CRUD scope
There will be some cases that we need to do some action to a resource that can’t really be semantically mapped to HTTP methods. Such as: hide/unhide a comment resource, clear server’s cached data, or resending a registration email for a user. There are a number of approaches:
- Restructure the action to appear like a field of a resource. This works if the action doesn't take parameters. For example an activated action could be mapped to a boolean activated field and updated via a PATCH to the resource.
- Treat it like a sub-resource with RESTful principles. For example, GitHub's API lets you star a gist with PUT /gists/:id/star and unstar with DELETE /gists/:id/star.
- Sometimes you really have no way to map the action to a sensible RESTful structure. For example, to search across multiple resources doesn't really make sense to be applied to a specific resource's endpoint. In this case, /search would make the most sense even though it isn't a resource or a noun. This is OK - just do what's right from the perspective of the API consumer, and if there are some thing that can’t be semantically understood above all, make sure it's documented clearly to avoid confusion. 

```
There are core principles that could rule out everything: 
"An API is a developer's UI, it's important to ensure the user's experience is thought out carefully." – 
so, use these (or general web) standards where they make sense for consumer’s usages. 
Try to make everything understandable on consumer’s first guess by following common standards, if that’s impossible and unavoidable, make sure they understand by writing it in the API documentations.  
```