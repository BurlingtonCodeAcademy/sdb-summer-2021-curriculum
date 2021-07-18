# Lab: CRUD Server!

Welcome to the DroidMaker3000! 

In this lab we will make a program that allows us to **create**, **read**, **update**, and **delete** entries from our Mongoose database, otherwise known as *CRUD*. 

## Getting Started

Create a new directory named `CRUD-example.js` and initialize it as an npm respository. Install the `mongoose` drivers.

```
mkdir CRUD-example.js
cd CRUD-example.js
npm init -y
npm install mongoose 
```

Next, make a new file called `CRUD.js`. Here we will configure the connection to our server by establishing a few key items:

 * our Mongoose import by requiring Mongoose
 * using the `.connect()` method, we connect to MongoDB and the server, which is `localhost:27017`
 * initialize a database through the connection constructor, which will be stored in a variable. 

in `CRUD.js`, add:

```javascript
const mongoose = require('mongoose')
mongoose.connect('mongodb://localhost:27017/test', { useNewUrlParser: true, useUnifiedTopology: true });
const db = mongoose.connection
```

We'll also bring in error handling for our database connection by binding an error message to our database connection variable. This will appear in our console if needed.

```javascript
db.on('error', console.error.bind(console, 'connection error'))
```

Because a CRUD application depends on user input, let's also add our readline imports and ask function.

```javascript
const readline = require('readline')
const readlineInterface = readline.createInterface(process.stdin, process.stdout)
function ask(questionText) {
    return new Promise((resolve, reject) => {
        readlineInterface.question(questionText, resolve)
    })
}
```

## Start function and Schema Creation

Now that we have the set up, let's create an async function to ask for user input and await the database connection. 

A schema outlines the expected data structure that will be inserted into a *collection*. They are used to create a *model*.

Our droid schema is *defined* by a number of definitions that are based on **SchemaTypes**. As a reminder, the SchemaType is the 'value' to the right of the `:`. The accepted SchemaTypes include `String`, `Number`,`Array`, `Boolean`, and more. A comprehensive list can be found [here](https://mongoosejs.com/docs/guide.html#definition).

```javascript
async function start() {
    const droidSchema = new mongoose.Schema({
        userName: String,
        droidName: String,
        color: String,
        astromech: Boolean,
        protocol: Boolean,
        affiliation: number,
        date: Date
    })
}

start()
```
## Models

Now that our data structure is defined by the schema, let's make some data using a model! 

**Models** are constructors built using the schema by enforcing the data structure defined there. It creates a collection based on the provided name. Instances of models are called *documents*.

Below, we define our model and set it to the variable name "Droid" by calling the mongoose method `.model()`. We pass to it the name of the collection the model is for, and the schema we want the model to use.

Here our model name is `Droid`. It uses the `droidSchema` from above. 

```javascript
const Droid = mongoose.model('Droid', droidSchema)
```

## User Input

The idea of CRUD capabilities is to allow a user to take certain actions to manipulate entries in a collection. In this instance we will handle user input by asking the user what action they want to take, passing it through an `if-else` loop, and returning the desired behavior.

Note: This is a bare-bones example that does nothing for error handling. It is simply meant to demonstrate the most basic data flow.

```javascript
let action = await ask('Welcome to the droid maker! What do you want to do? (Create, Read, Update, Delete)   ')
```
# CREATE !

## Assigning User Input

If first we want to bring our droid to life, check that the user has entered "Create" as their command.

```javascript
if (action === 'Create') {}
```

Next, define variables that correspond to the fields found in our schema and set them to `await ask()` questions in which the answers will be stored. 

```javascript
let userName = await ask('What is your name?   ')
let droidName = await ask('What is the name of the droid you want to create?   ')
let droidColor = await ask('What is your droid\'s color(s)?   ')
```

Some of these questions will be conditional based on the droid type. 
    -  If the droid is an astromech, the application should not ask if the droid is a protocol droid, and vice versa. 
    - Regardless of choice, the application should then ask how the droid is affiliated, and a new Date instance should be generated and assigned to the date
    -  Don't forget to set those variables outside of the loop, or else they will be lost in scope later on.

Because every field of our schema requires data, you'll need to assign the whichever droid type wasn't chosen to the corresponding boolean value.

```javascript
let affiliation
let protocol
let date

if (astromech === 'N') {
    astromech = false
    protocol = await ask('Is your droid a protocol droid?   ')
    protocol = true
    affiliation = await ask('What faction is your droid? 1 for Rebel Alliance, 2 for Empire.   ')
    date = new Date()
} else if (astromech === 'Y') {
    astromech = true
    protocol = false
    affiliation = await ask('What faction is your droid? 1 for Rebel Alliance, 2 for Empire.   ')
    date = new Date()
}
```

And finally, an else block to catch incorrect input.

```javascript
else {
    console.log('That does not compute. Try again!')
}
```

## Storing User Input

Great! We have our user input. Now we'll create a new entry with it. 

Create a variable and use the `new` keyword to create a new instance of the `Droid` model. Here we've named the variable `response` as it holds the responses of the user.

```javascript
 const response = new Droid({
    userName: userName,
    droidName: droidName,
    droidColor: droidColor,
    astromech: astromech || null,
    protocol: protocol || null,
    affiliation: affiliation,
    date: date,
})
```

Finally, we will save this new droid and send a message to the console to let our user know. We do so by awaiting the user response with the `await` keyword, using the `.save()` method, and a `console.log()`.

```javascript
await response.save();
console.log('your droid has been created!')
```

# READ !

Next up, the ability to see all items in our Droid collection. 

First, verify user input within our async `start()` function. 

```javascript
} else if (action === 'Read') {
```

Next, we want to await our database connection. We'll be asking it to look for *all* items in our collection using the `.find()` method. Once returned we will store them in a variable that will be printed to the console.

```javascript
let allDroids = await Droid.find({})
console.log(allDroids)
```

# UPDATE !

Now that we've seen all of our entries, let's choose one to update!

First, verify user input within our async `start()` function. 
```javascript
} else if (action === 'Update') {
```

Again, gathering all of our collection's entries, print them to the terminal.

```javascript
let allDroids = await Droid.find({})
console.log(allDroids)
```

Next, using the `await ask()` function, get the following input from the user:
 - which entry should be updated
 - which feld should be updated
 - and what the new value should be

Store each in a variable for later use.

 ```javascript
let updateTarget = await ask('What is the ID of the droid do you want to update?   ')
let updateField = await ask('What field do you want to update?   ')
let update = await ask('enter a new value   ')
```

Now that we have user input, let's update the entry using the `updateOne()` method. We will pass in the `updateTarget` variable for our entry's `_id`, the `updateField` variable for the key of the value that we want changed, and the `update` variable for the value of what we want changed.

Because our entries are saved as objects we will need to use curly brackets to access fields within them. We will also be using the atomic operator `$set`, which helps prevent accidentally overwriting all of our documents that share the same `updateField` and `update` key value pair.

Like our other methods, it will need to be awaited. Print a message to the user so they know the entry was updated successfully.

```javascript
await Droid.updateOne({ _id: updateTarget }, { $set: { [updateField]: update } })
console.log('your entry has been updated!')
```

# DELETE !

Our last capability should be to delete an entry. 

First, verify user input within our async `start()` function. 
```javascript
} else if (action === 'Delete') {
```
Again, gathering all of our collection's entries, print them to the terminal.

```javascript
let allDroids = await Droid.find({})
console.log(allDroids)
```

Next, using the `await ask()` function, ask the user which entry to delete, and store the user input in a variable for later use.

```javascript
let target = await ask('what is the ID of the entry do you want to delete?   ')
```

Now that we have the user input, let's use the `.deleteOne()` method to remove the entry in our collection. Identify the entry by passing the id number stored within the `target` variable. 

Like our other methods, it will need to be awaited. Print a message to the user so they know the entry was deleted successfully.

```javascript
await Droid.deleteOne({ _id: target })
console.log('your entry has been deleted')
```

# LAST STEP !

Because we are operating in an `if-else` loop that validates user input from our async `start()` function, close out the loop by adding a catch-all should the user try using an invalid command. 

```javascript
 } else {
    console.log('invalid entry, try again')
}
```

And lastly, close out the function with a `process.exit()`. If you haven't declared it already, don't forget to call the `start()` function at the bottom of your application!

```javascript
   process.exit()
}
```