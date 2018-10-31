---
layout: default
title:  "Containers"
date:   2018-09-14 17:50:00
categories: cs
---

Virtualization is useful, because it provides several benefits. Sandboxing, elasticity, resource sharing and higher utilization
are among those. System-level virtualization, such as that provided by hypervisors like vmkernel, Xen, etc. are expensive. 
OS-level virtualization is a cheaper way of providing the VM abstraction, and this is what containers essentially provide.
They provide a private namespace, filesystem and network interfaces. This allows for faster deployment, portability and a 
consistent environment.

Docker is a platform for running containers, which separates applications from their infrastructure, allowing you to easily
develop, ship and run applications. The docker daemon, dockerd, manages Docker objects, images, network and volumes.
The Docker CLI talks to the docker daemon using the REST API. A Docker registry stores docker images. They may be public or
private.

Docker runs on the following underlying technology:
  * `cgroups` to limit an application's access to a set of resources
  * `unionfs` to create lightweight file-system "layers"
  * `libcontainer` format for containers




References:
[1] https://docs.docker.com/engine/docker-overview/
