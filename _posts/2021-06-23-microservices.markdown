---
layout: default
title:  "Microservices"
date:   2019-12-03 09:09:00
categories: webdev
---

# Microservices
Microservices architecutre consist of constructing an application that consistes of serveral services that are loosely-coupled, independently testable/maintainable/deployable and centered around business needs.

It makes sense for most businesses to start out as a monolith and then eventually transition to microservices as the team scales. Not necessarily when the number of users scale. Monoliths are easier to develop, deploy and test. They make sense when the teams are smaller and velocity is more important.

How to ensure you can smootly transition from a monolith to microservices?
 * reduce the number of tangled dependencies
 * reduce shared resources, global variables
 * write more independent, self-sufficient modules

The transition starts from moving one component out at a time, starting from less-critical services. All new features are built as microservices.

References:

[1] https://microservices.io/

[2] https://www.youtube.com/watch?v=rckfN7xFig0
