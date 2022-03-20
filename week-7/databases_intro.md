# Databases

> *database* (n.) -
> a structured set of data held in a computer, usually organized so that it can be easily accessed, managed and updated

---

# Database Examples

|Relational (SQL)|Document (NoSql)|Object-Oriented|Graph|Filesystem|
|---|---|---|---|---|
|  |

|Style|Examples|
|---|---|
|Relational (SQL) | Oracle, MySQL, PostgresQL, Microsoft SQL Server |
| Document DBs (NoSQL) |  MongoDB,  CouchDB,  Google BigTable,  Apache Cassandra |
| Object-Oriented (OODB) |  Smalltalk/Gemstone, Prevayler |
| Graph DBs | Neo4j,  GraphQL (*) |
| File Systems |  any Unix or DOS filesystem,  IPFS |

(*) GraphQL not a database *per se*, but a query language *for* graph DBs and APIs

---
 
## Document Database

A **document database** (aka NoSQL) stores information in *documents*.
- Similar to JSON objects

---

## Database concepts

  * Connection
  * Collection
  * Record
  * Primary Key
  * CRUD
  * Index
  * Query / Search
  * Transaction
  * Blob

---

# Connection

- Communication between client and server involves more than a single request and response.
- Generally, the client 
    - connects to a server early on
    - authenticates itself 
    - then maintains the connection 
      - doesn't need to authenticate on later requests

Stateful connections enable other features like *transactions*, *caching*, and *load balancing*.

---

## Primary Key

**Primary Keys** are included in records to be able to differentiate them.

They allow records to be nearly identical without you losing track of them.

---

## CRUD

The four basic database operations:

|Operation|Mongo|
|---|---|
|**C**reate| `insertOne`, `insertMany`, etc.  |
|**R**ead | `findOne`, `find`  |
|**U**pdate  | `updateOne`, `updateMany`  |
|**D**elete | `deleteOne`, `deleteMany`, `findOneAndDelete`, etc.  |

---

# Query / Search

**Query** is the term used for the "ask" made of the database
- What was the database asked to do?

**Search** is the act of actually doing what was asked for in the query.

---

# Transaction

**Transactions** allow us to handle different queries happening simultaneously.

- For example:
    - When making a transfer between two bank accounts, 
    - You want the withdrawal and the deposit to happen *as one transaction*.

- If any step in the transaction fails, 
    - The transaction is *rolled back*.
    - No other connection will ever see the changes.

- If everything succeeds, 
    - The transaction is *committed*.
    - Other connections can see all the changes.

---

# Blob

**BLOB** stands for "Binary Large Object" but it is also a good metaphor.

A BLOB is *any piece of data* that the database can't describe: 
- does not look inside it
- doesn't know its value
- can't sort based on it
- allows it to be arbitrarily small or large, etc.

Note: JSON without using MongoDB does not support this.

---

# Schema

A **schema** defines the types, names and valid values of a database.

In document databases, it's up to the application developer to ensure the data conforms to the application's needs. 

You can use libraries such as [mongoose](https://mongoosejs.com/) for schema validation.

> Note: This might remind you of form validation and is often directly connected to that. 
