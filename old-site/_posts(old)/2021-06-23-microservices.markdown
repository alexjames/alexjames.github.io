---
layout: default
title:  "Microservices"
date:   2019-12-03 09:09:00
categories: webdev
---

# Microservices
Microservices architecutre consist of constructing an application that consistes of serveral services that are loosely-coupled, independently testable/maintainable/deployable and centered around business needs. These services communicate with each other over the network using gRPC, REST, etc. Each service will typically have its own database. Fundamentally, it is a divide-and-conquer approach to tackling large complex systems in a scalable way.

It makes sense for most businesses to start out as a monolith and then eventually transition to microservices as the team scales. Not necessarily when the number of users scale. Monoliths are easier to develop, deploy and test. They make sense when the teams are smaller and velocity is more important. However, as you transition from monoliths to microservices, complexity moves from source code to operations. Managing several services is hard, which is why observability becomes important. A simple system does not need to be architected as a microservice.

How to ensure you can smootly transition from a monolith to microservices?
 * reduce the number of tangled dependencies
 * reduce shared resources, global variables
 * write more independent, self-sufficient modules
 * have each feature use a separate database namespace/tables, so that they can be torn out easily later

The transition starts from moving one component out at a time, starting from less-critical services. All new features are built as microservices.

CI/CD is an important requirement for microservices to be easily deployed. So is logging, tracing, auditing, metrics and monitoring for observability.

Think about having a unified tech stack so there's fewer languages and frameworks to maintain.

References:

[1] https://microservices.io/

[2] https://www.youtube.com/watch?v=rckfN7xFig0

[3] https://towardsdatascience.com/microservice-architecture-and-its-10-most-important-design-patterns-824952d7fa41

[4] https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd

