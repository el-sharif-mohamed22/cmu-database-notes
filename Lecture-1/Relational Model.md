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
- Hard to add a new field, as we will need to change the whole file [Schema](#what-is-schema-)

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

---
## Relational Model 
- Ted Codd noticed that people were rewriting **DBMSs** every time they wanted to change the *Physical layer*, so in *1969* he proposed the relational model to avoid this.

## What is the Relational Model? 
- The relational data model defines a database abstraction based on relations to avoid maintenance overhead.
- It has 3 key points:
    1. Store database in simple datastructure.
    2. Access data through high-level language, DBMS figures out best execution strategy.
    3. Physical storage left up to the DBMS implementation.

## What are the 3 concepts that Relation Model proposed? 
1. **Structure**
    - The definition of relations and their contents.
    - This is the attributes the relations have and the values that those attributes can hold.
2. **Integrity**
    - Ensure the database's contents satisfy [constraints](#constraints)
    - An example constraint would be that any value for the year attributes has to be a number.
3. **Manipulation**
    - It's the programming interface that allows us to update and change in the database contents.

---
## What does the word "Relation" mean?
- Relation is basically an *unordered set* that contains the relationship of attributes that represent entities.
- Making it *unordered* allow us the **DBMS** to store them in any way it wants, allowing for optimization.
- It could have repeated elements in a relation.
- Finally, We could think of a Relation to be a table of rows and columns that has values represents some aspect of real-world.

## What is a tuple? 
- A tuple is a set of attribute values (domain) in the relation.
- Values could be atomic or scalar and also could be lists or nested data structures.
- Every attribute could be a special value, `NULL` which means for a given tuple the attribute is undefined.

---
ℹ️ **NOTE**
> A relation with $n$ attributes is called an $n-$ ary  relation, and it is equivalent to a table with $n$ columns.

---
## What is Keys? 
- We have 2 types of keys:
    1. Primary Keys.
    2. Foreign Keys.
- Primary Keys
    - It is the key which identifies a single tuble, and it has to be unique for each tuple.
    - Some **DBMSs** automatically create an internal primary key if a table doesn't define one.
- Foreign Keys
    - Specifies that an attribute from one relation or table maps to a tuple in another relation or table.
## What is Identity Column?
- It is a column that holds the unique values of the primary keys for each tuple in the relation or table.

## Constraints
- It is a user-defined condition that must hold for any instance of the database.
- It can validate data within a single tuple or across entire relations.
- **DBMSs** prevents modifications that violates any constraint.
- Global assertions in SQL could be made but, it is rarely used as it is too slow.

---

## Data Manipulation Languages (DML)
- Methods to store and retrieve information from a database.
- There are 2 classes of languages for this:
    1. Procedural ([Relational Algebra](/Lecture-1/Relational%20Algebra.md))
        - The query specifies the high-level strategy the **DBMS** should use to find the desired result based on sets/bags
    2. Non-Procedural (Declarative "Relational Calculus")
        - The query specifies only what data is wanted and not how to find it. 