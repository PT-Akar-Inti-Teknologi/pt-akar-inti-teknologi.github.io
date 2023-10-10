---
layout: default
title: Architectural Design Standards
permalink: /standards/others/architecture
parent: Others
grand_parent: Standards
nav_order: 1
---

# Architectural Design Standards
{: .no_toc }

## Tools

Recommendation tool: Draw.io https://app.diagrams.net/

## What needs to be in the architectural design?

Recommended to be included in the architectural design:

- Type of client used (mobile / web / desktop, etc.)
- Use of API Gateway (Optional, recommended when using microservice architecture)
- Add a proxy / ingress to the architecture when accessing from the client to the server.
- Place the projects we create (FE / BE) into one large box that indicates that the project is within the scope of our work.
- Place third-party components outside the large box #4 to indicate that this part is outside our scope and we are integrating with the 3rd party.
- Place services inside box #4, such as databases, Redis, and others, which will become our scope to manage/install on the server.
- Draw the BE (Back-End) according to its architectural shape:
  - For microservice-based BE, draw the services to be created and relate them to third parties or internal services (such as databases) used.
  - For monolithic BE, draw only one service representing that the application is monolithic and relate it to relevant services.

## Example

![image](https://github.com/PT-Akar-Inti-Teknologi/ait_development_standard_assets/blob/main/Architecture/2.jpg?raw=true)