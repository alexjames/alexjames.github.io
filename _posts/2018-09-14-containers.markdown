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
