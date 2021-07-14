
# Setup
* Download [MongoDB Community Server](https://www.mongodb.com/try/download/community)

This should include MongoDB Compass.

Compass is a GUI, or *graphical user interface*, that simply provides a platform to view your data without the initial need for knowing MongoDB [query syntax](https://docs.mongodb.com/manual/tutorial/query-documents/).

This makes it a great place to start!

---

# MongoDB Overview

* document database (NoSQL)
* horizontal sharding => can theoretically serve *trillions* of records
* uses JavaScript for data definition and manipulation
* built-in map-reduce for dynamic collections
* indexing on fields by value or free-text search 

> "Mongo is not a toy, although it can be fun to play with." - Josh Burke

---

# Concept: Database

to connect to a database you need a Mongo URI (or URL) identifying the server, port, etc.:

Connection URL format:

```
mongodb://username:password@host/database
```

for example

```
mongodb://mydatabasehost.com:27017/example_db
```

or (locally)

```
mongodb://localhost:27017/example_db
```
If no database with the provided name is given, it will default to `test`.
Note that the term "database" is overloaded: it refers to either:

1. a single MongoDB *process* hosting many data sets
2. a single MongoDB *data set* containing many related *collections*

---

# Concept: Collection

A *collection* holds documents. 

Many collections can live in a *database*.

This is analogous to a *table* in SQL.

---

# Concept: Document

In MongoDB, a *document* is essentially a single JavaScript *object*

Like in a relational database, a document can be *created, read, updated, deleted, indexed, searched for*, ...

*Unlike* in a relational database, a document can contain *any* value for its fields, *including arrays and nested objects*.

This nesting and type-flexibility makes it very appropriate to store whatever JavaScript objects your app uses, without needing to devise a *mapping* between nested objects and joined relational tables.

---

# Drivers
* MongoDB has its own [query syntax](https://docs.mongodb.com/manual/tutorial/query-documents/) that, while very similar to JavaScript at times, has its own rules and structure! 

This allows MongoDB to be used with a number of languages through the use of *drivers*, which are language-specific! For our case, we'll be using MongoDB's **Node.js driver**, because we're JavaScript people, and we're working server side.

[Full list of drivers](https://docs.mongodb.com/drivers/)

---

# View it in Compass

Select the database and collection on the side and...

![Compass2](/images/Compass2.png)

Voila! But what's that `_id` thing?

---

# Concept: ObjectId

- `_id` is assigned by Mongo when a document is inserted
- `ObjectId` is a factory function that either generates a new id, or transforms a given string into a Mongo ID object
