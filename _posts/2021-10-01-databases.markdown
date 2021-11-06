---
layout: default
title:  "Databases"
date:   2019-12-03 09:09:00
categories: sysdesign
---

Databases are at the heart of modern computer applications. Most applications that do anything useful will probably need the ability to store and query data. Database management systems provide this ability. They are the common thread underlying everything from the smallest of phone applications to humongous distirbuted systems spanning several continents.

#### Types of Data
What type of data would we want to store in a database? Anything from phone records to entire books. We might also want to store videos, images or music. Computers need data to be in digital format to understand it. From their perspective, anything that can be stored in a file can probably be stored in a database.

It's not just useful to store data, when we can also generate useful insights from it. Let's say you have a folder on your desk with all your utility bills. If you wanted to know the months your bill was below a certain amount, you'd have to look through every bill in the folder. Databases provide ways to quickly query data which helps save time. Different databases are optimized for storing, retrieving and querying different kinds of data. The choice of DBMS depends on your specific application. While most general-purpose databases are good for msot things, you can gain some benefits from using ones better suited for the problems you're trying to solve. 
With digitization, you could have it all in a small USB Flash Drive. Or even not at all, and have Google or Dropbox store it for you on the cloud.


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

