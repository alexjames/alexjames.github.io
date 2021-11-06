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

#### When not to use a DBMS
There are many cases when it's feasible to not use a full-blown DBMS to get the job done. Writing data directly to files can suffice depending on your needs. CSV, JSON, YAML and XML are popular formats. While the usage of such formats can make the creation and reading of such files easier, updating becomes a challenge. More often than not, you'll have to re-write the whole file during update operations. This might not be a big deal and in fact, it's very common for applications to have their configuration files stored in these formats.

There are several problems that storage on a file-system won't address though -
 * Integrity - lots of specialized logic to do anything, machine crashes could lead to data corruption
 * Scale - The file system approach might work fine for 10 records, it is grossly unscalable for ten million records
 * Portabliity Support - If two programs try to update the database at the same time, you could have inconsistent or corrupt file
 * Replication - Disaster recovery

A DBMS allows the creation, management and administration of databases without worrying about the internal storage. There are a
variety of differnt databases specialzing in different applications. As a database architect, you have to know the procs and cons of each type.

Data Model
- Relational
- Key Value
- Graph
- Document
- Columnar
- Array/Matrices

