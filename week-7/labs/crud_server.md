# Lab: CRUD Server!

Welcome to the Robot Factory! 

In this lab we will make a program that allows us to **create**, **read**, **update**, and **delete** entries from our Mongoose database, otherwise known as *CRUD*. This will take the shape of creating a robot factory in our terminal.

## Getting Started

Create a new directory named `CRUD-robot-factory` and initialize it as an npm respository. Install mongoose.

Next, make a new file called `CRUD.js`. Here we will configure the connection to our server by establishing a few key items:

 * Our Mongoose import by requiring Mongoose
 * Using the `.connect()` method, we connect to MongoDB and the server, which is `localhost:27017`, and the database, which is `/factory`
 * Initialize a database through the connection constructor, which will be stored in a variable. 

in `CRUD.js`, add:

```javascript
const mongoose = require('mongoose')
mongoose.connect('mongodb://localhost:27017/factory');
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

Let's create an async function to ask for user input and await the database connection. 

A schema outlines the expected data structure that will be inserted into a *collection*. They are used to create a *model*.

Our robot schema is *defined* by a number of definitions that are based on **SchemaTypes**. As a reminder, the SchemaType is the 'value' to the right of the `:`. The accepted SchemaTypes include `String`, `Number`,`Array`, `Boolean`, and more. A comprehensive list can be found [here](https://mongoosejs.com/docs/guide.html#definition).

```javascript
async function start() {
    const robotSchema = new mongoose.Schema({
        creatorName: String,
        robotName: String,
        robotColor: String,
        killer: Boolean,
        friend: Boolean,
        serialNumber: Number,
        date: Date
    })
}

start()
```
## Models

Now that our data structure is defined by the schema, let's make some data using a model! 

**Models** are constructors built using the schema by enforcing the data structure defined there. It creates a collection based on the provided name. Instances of models are called *documents*.

Below, we define our model and set it to the variable name "Robot" by calling the mongoose method `.model()`. We pass to it the name of the collection the model is for (`'robots'`), and the schema we want the model to use (`robotSchema`).

Here our model name is `Robot`. It uses the `robotSchema` from above. 

```javascript
const Robot = mongoose.model('robots', robotSchema)
```

## User Input

The idea of CRUD capabilities is to allow a user to take certain actions to manipulate entries in a collection. 

In this instance we will handle user input by asking the user what action they want to take, passing it through an `if-else` loop, and returning the desired behavior.


```javascript
let action = await ask('Welcome to the robot factory! What do you want to do? (Create, Read, Update, Delete)   ')
```
# (C)reate

## Assigning User Input

If we want to create a new robot:

* Check that the user has entered "Create" as their command and then begin asking questions.
* Define variables that correspond to the keys found in our schema; ask the user for what value they want the key to have.

```javascript
 if (action === 'Create') {
        let creatorName = await ask('Who is the creator?')
        let robotName = await ask('Designate this robot?')
        let robotColor = await ask('What color is this robot?')
        let friend = await ask('Is this robot a friend? Enter Y or N')
```

Some of these questions will be conditional based on the robot type. 
-  If the robot is a friend robot, the application should not ask if the robot is a killer robot, and vice versa. 
- Regardless of choice, the application should then ask for the robot's serial number, and a new Date instance should be generated and assigned to the date
-  Don't forget to set those variables outside of the loop, or else they will be lost in scope later on.

Because every field of our schema requires data, you'll need to assign the whichever robot type wasn't chosen to the corresponding boolean value.

Once the robot type is assigned, you will need to follow up by asking the serial number and creating a date.

```javascript
if (friend === 'N') {
    friend = false
    killer = true
    console.log('Oh no! A killer robot!')
    serialNumber = await ask('What is the serial number?')
    date = new Date()
```

## Storing User Input

Great! We have our user input. Now we'll create a new entry with it. 

Create a variable and use the `new` keyword to create a new instance of the `Robot` model. Here we've named the variable `response` as it holds the responses of the user.

```javascript
 const response = new Robot({
    creatorName: creatorName,
    robotName: robotName,
    robotColor: robotColor,
    friend: friend || null,
    killer: killer || null,
    serialNumber: serialNumber,
    date: date,
})
```

Finally, we will save this new robot and send a message to the console to let our user know. We do so by awaiting the user response with the `await` keyword, using the `.save()` method, and a `console.log()`.

```javascript
await response.save();
console.log('Your robot has been created!')
```

# (R)ead

Next up, the ability to see all items in our 'robots' collection. 

First, verify user input within our async `start()` function. 

```javascript
} else if (action === 'Read') {
```

Next, we want to await our database connection. We'll be asking it to look for *all* items in our collection using the `.find()` method. Once returned we will store them in a variable that will be printed to the console.

```javascript
let allRobots = await Robot.find({})
console.log(allRobots)
```

# (U)pdate

Now that we've seen all of our entries, let's choose one to update!

First, verify user input within our async `start()` function. 
```javascript
} else if (action === 'Update') {
```

Again, gathering all of our collection's entries, print them to the terminal.

```javascript
let allRobots = await Robot.find({})
console.log(allRobots)
```

Next, using the `await ask()` function, get the following input from the user:
 - which entry should be updated
 - which field should be updated
 - and what the new value should be

Store each in a variable for later use.

 ```javascript
let updateTarget = await ask('What is the ID of the robot you want to update?   ')
let updateField = await ask('What field do you want to update?   ')
let update = await ask('Enter a new value   ')
```

Now that we have user input, let's update the entry using the `updateOne()` method. We will pass in the `updateTarget` variable for our entry's `_id`, the `updateField` variable for the key of the value that we want changed, and the `update` variable for the value of what we want changed.

Because our entries are saved as objects we will need to use curly brackets to access fields within them. We will also be using the atomic operator `$set`, which helps prevent accidentally overwriting all of our documents that share the same `updateField` and `update` key value pair.

Like our other methods, it will need to be awaited. Print a message to the user so they know the entry was updated successfully.

```javascript
await Robot.updateOne({ _id: updateTarget }, { $set: { [updateField]: update } })
console.log('Your robot has been updated!')
```

# (D)elete 

Our last capability should be to delete an entry. 

First, verify user input within our async `start()` function. 
```javascript
} else if (action === 'Delete') {
```
Again, gathering all of our collection's entries, print them to the terminal.

```javascript
let allRobots = await Robot.find({})
console.log(allRobots)
```

Next, using the `await ask()` function, ask the user which entry to delete, and store the user input in a variable for later use.

```javascript
let target = await ask('what is the ID of the entry do you want to delete?   ')
```

Now that we have the user input, let's use the `.deleteOne()` method to remove the entry in our collection. Identify the entry by passing the id number stored within the `target` variable. 

Like our other methods, it will need to be awaited. Print a message to the user so they know the entry was deleted successfully.

```javascript
await Robot.deleteOne({ _id: target })
console.log('your entry has been deleted')
```

# Error handling and ending the program

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

# Going Further

* Think back to Zorkington. How can you loop the program so that, once an action is complete, the user can complete another without rerunning the program?

* What if a user meant to create a friend robot instead of a killer robot? How could you change the logic to ask the user to confirm they intended to make their robot killer?

* Right now, the user has to input the exact id and property in order to update the robot. How could you make this more user friendly? Let the user give the name of the robot to update (instead of the id) AND let them type the property in natural language ("serial number" instead of "serialNumber").

* Translate this lab to an Express server with a React front end, much like we did in the "Fetching Data" lab.
