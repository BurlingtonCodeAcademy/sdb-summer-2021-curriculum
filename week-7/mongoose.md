# Using Mongoose for Schema Validation

When writing to a database, it is often important to ensure the data is as expected.

Enter schema-validation with **Mongoose**. 

[Mongoose](https://mongoosejs.com/) is a library that provides "a straight-forward, schema-based solution to model your application data."

---

# Mongoose: Getting Started

* Mongoose replaces the `mongodb` driver
* Runs `mongodb` queries on your behalf

```
mkdir mongoose-example
cd mongoose-example
npm init -y
npm install mongoose
```

---

# Getting Started, cont.
Create a file called `mongoose.js`
In it, write the following code.

`example_db` in the connection string `"mongodb://localhost:27017/example_db"` denotes a database name, and can be anything you choose. 

```javascript
const mongoose = require('mongoose')
/* 
pass { useNewUrlParser: true, useUnifiedTopology: true } as a second 
argument to the connect method to avoid deprecation warnings
*/
mongoose.connect('mongodb://localhost:27017/example_db') 
const db = mongoose.connection

db.on('error', console.error.bind(console, 'connection error:'))
```

---

# Concept: Schemas

A schema outlines the expected structure of the data that will be inserted into a *collection*

A database schema can also define *methods* on the documents being inserted. 

* *defines* what that data should look like, and how it should behave.
* used to create a *model* 
* definitions are based on `SchemaTypes`

---

# Example Schema 

```javascript
const studentSchema = new mongoose.Schema({
    name: String,
    age: Number,
    hobbies: Array,
    current: Boolean
})
```
[Setting up your configuration object](https://mongoosejs.com/docs/guide.html#definition).

---

# Concept: Model

While the definition of the data's structure is held in the Schema, a *Model* actually handles the work.

* an object built by Mongoose using the *schema* you made 
* *enforces* your schema's types (e.g. `String`)
* creates a collection based on provided name
* instances of models are documents

---

# Using a Schema to Build a Model

```javascript
// Student Model
const Student = mongoose.model('Student', studentSchema)

// Fatima Document made from Student Model
const fatima = new Student({ name: 'Fatima', age: 29, hobbies: ['jumprope', 'd&d', 'coding'] })
// call the save() method on a model instance to insert it to the collection 
fatima.save()
```

---

# Models and Error Handling

```javascript
fatima.save((err, fatima) => {
    if (err) {
        return console.error(err)
    } else {
        return console.log("document inserted!")
    }
})
```

---

# Models and Collections

* Creating an *instance* of a model makes a document 
* Using `.save()` saves that document to a collection
* That *collection* is a lowercase, pluralized version of the Model name 
    - Model: `Student`
    - Collection: `students`
* The collection can be queried directly with methods from the Model:
    - supports MongoDB query syntax
    - takes a callback for error handling

---

# Using Model Methods to Make Queries

```javascript
Student.find({ name: 'Fatima' }, (err, results) => {
    if (err) {
        return console.log(err)
    } else {
        return console.log(results) // => [{name:'Fatima', age: 29, ...}]
    }
})
```

Note: You can still use **Compass** to verify your code is working. 

---

# Mongoose Validation Errors

Let's create a `Student` instance and intentionally give it bad data:

```js
let wei = new Student({ name: "wei", age: "thirty-two", hobbies: ["carpentry", "archery"] })

wei.save()

// `Student validation failed: age: Cast to Number failed for value "thirty-two" at path "age"`
```
