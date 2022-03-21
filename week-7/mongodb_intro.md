# Software

During orientation, we downloaded MongoDB and Mongo Compass.

---

# MongoDB 

* Document database 
* Horizontal sharding => can theoretically serve *trillions* of records
* Uses JavaScript for data definition and manipulation
* Searchable 
    * fields by value 
    * free-text 

> "Mongo is not a toy, although it can be fun to play with." - Josh Burke

---

# Concept: Database

To connect to a database you need a Mongo URI:

Connection URL format:

```
mongodb://username:password@host/database
```

Remote:

```
mongodb://mydatabasehost.com:27017/example_db
```

Local:

```
mongodb://localhost:27017/example_db
```

Default databse is "test"

---

# Concept: Collection

A **collection** holds documents. 

Many collections can live in a *database*.

---

# Concept: Document

In MongoDB, a *document* is viewable in **JSON** or **BSON**.
- BSON allows for file storage.

- A document can be *created, read, updated, deleted, indexed, searched for*, etc ...

- Their fields can contain any values.

- Documents can hold other documents. 

---

# Drivers
* MongoDB has its own [query syntax](https://docs.mongodb.com/manual/tutorial/query-documents/) that is *similar* to JavaScript.

Programming languages use *drivers* to interact with MongoDB. 
We'll use MongoDB's **Node.js driver**.

[Full list of drivers](https://docs.mongodb.com/drivers/)

---

# View it in Compass

Select the database and collection on the side and...

![Compass2](https://res.cloudinary.com/btvca/image/upload/v1626359023/curriculum/Compass2_azhhmk.png)

Voila! But what's that `_id` thing?

---

# Concept: ObjectId

- `_id` is assigned by Mongo when a document is inserted
- `ObjectId` is a factory function that either generates a new id, or transforms a given string into a Mongo ID object
- If we want to reference a document by `_id` we need to make sure it's a Mongo ID object.
