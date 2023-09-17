## What is a Database ? 
- Organized collection of data that is related to each others, and have some aspects of the real-world.
## Where could database be used in ?
- Database are the core component of most computer applications.
---
## What is the easiest way to implement a database ? 
- The easiest way is called **"Flat File Strawman"**, in this way we store our data as comma separated value (**CSV**) 
- Example for a **CSV** file
```txt
"Wu-Tang Clan", 1992, "USA"
"Notorious BIG", 1992, "USA"
"GZA", 1990, "USA"
```

## What are the issues with this database implementation ? 
- It has a low *Efficiency* as the file needs to parse the whole file for storing a particular record.
- *Data Integrity* as you could reference non-existent record for an attribute or parameter in your database, for example "Referencing a non-existent artist in the album file" 
    - We have no rule controlling our data how should it look like every time adding a record to the database.
- Hard to add a new field, as we will need to change the whole file [Schema](#What is Schema ?)

- *Concurrency* We have no controll over multithreading on our simple database, if 2 threads try to update the same record, we could have data corruptions and inconsistent readings.

- We are limited only with using the **CSV** files.

- *Durability* If the program crashes while updating a record, This could make data loss, data corruption and inconsistent state  for records, all these makes using this implementation of database are so hard to use as there is no crash recovery could be done by these systems.

--- 
## What is a Database Management System (DBMS)? 
1.  A **DBMS** is a software that allows applications to store and analyze information in a database.
2. A general-purpose **DBMS** is designed to allow the defintion, creation, querying, update and administration of databases in accordance with some data model.

- In real life we need to specify which **DBMS** that could serve our needs while building the application.
- We will find a pretty much ready-to-use **DBMS** that could fit our use case, so we won't have to build our own in most cases.

## What is a data model ? 
- It is a collection of concepts for describing the data in database.
- It is also could be defined as the high level abstraction of how data looks like in the database.
### Data Model Examples
![](https://static.javatpoint.com/dbms/images/data-models.png)

---
## What is Schema ?
- A schema is a description of a particular collection of data based on a data model.
- It descripes each entity in database using a given data model.

## What is the difference between the logical layer and the physical layer ? 
- The *Logical Layer* describes which entities and attributes the database has while the *Physical Layer* is how those entities and attributes are being stored.
- in Early **DBMSs**, The physical layer was defined in the application code, so if we wanted to change the physical layer the application was using, we needed to change the whole code to match the new physical layer.

