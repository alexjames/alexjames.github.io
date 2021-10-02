---
layout: default
title:  "Databases"
date:   2019-12-03 09:09:00
categories: sysdesign
---

Databases are at the heart of modern computer applications. Anytime you use an application that stors and accesses data, it probably has a database underneath.
How exactly would applications store data?

### File System and Flat Files
#### Store as a Text file, CSV
One file per entitys. Traverse and parse files.

#### JSON files/YAML/XML
You have to read and write the whole file for updates.

Advangaes are they are easy to deal with and are commonly used as configuration files.

Probles with files
Integrity - lots of specialized logic to do anything, machine crashes could lead to data corruption
Scale - ten records vs ten million
Portabliity - Using the database with a different applicaiton, you'd have to reimplement the logic to access and manage
Concurrency - If two programs try to update the database at the same time, you could have inconsistent or corrupt file
Replication - Disaster recovery

A DBMS allows the creation, managemening and administraiton of databases without worryting abotu the intrenal storage. There are a
vaeritye of differetn databases specialzing in different applications. As a database architect, you have to know the procs and cons of each type.

Data Model
- Relational
- Key Value
- Graph
- Document
- Columnar
- Array/Matrices

