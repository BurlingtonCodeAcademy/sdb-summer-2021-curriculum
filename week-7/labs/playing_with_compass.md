# Lab: Exploring with Compass

This is MongoDb's GUI tool. Let's open it up and see what it can do!

*(Don't have it installed? [Click here](https://www.mongodb.com/try/download/compass))


## Connect 

First, open Compass and click on the green "Connect" button; it defaults to `localhost` for ease of use, though we can connect it to a MongoDB host as well. For now, let's keep it simple! 

Upon loading up on `localhost:27017`, you'll see a large white field and a grey sidebar on the left. Both areas contain our database names; the white box shares granular information, and the sidebar nav acts in part as a directory view.

## Collections

Find the database named `test` and open it. This is where collections that you establish through localhost applications will be stored, as `test` is the default database for locally established connections unless directed otherwise. Most of this week's labs and codealongs will connect to MongoDB databases and collections via `localhost`. You'll be able to find the different *collections* we create here.

A *collection* is any number of documents (or entries, or records) that are are related. In MongoDB these records are defined by *schemas*, which are data structures that are used by *models* that create individual collection entries. These get stored in the collection, which lives inside of a *database*. As we create more collections in class, you'll see that multiple collections can live inside of a database.

## Collections Con'td
Right now we don't have any collections. Create your own by clicking the "Create Collection" button at the top left of the white field. You will be prompted to name the collection. Do so, and leave the boxes below unchecked.

Ta da! A wild collection has appeared.

In the collection you just created, try running through the following exercises:

# CREATE a Document: 
>Remember, a document is another way to say entry or record. 

Click the 'Add Data' button to open a dropdown. Here you'll be able to add multiple documents at once to your collection through JSON or CSV files, or by adding them  individually. Let's do the latter by selecting "Insert Document".

In this method, documents can be written as JSON or field-by-field. When the prompt to add a document appears, you can toggle through the two types of input by pressing the buttons on the top left of the pop-up. 

Notice the curly brackets around _id's value? MongoDB will automatically generate an ObjectId for your document unless you provide an _id of your own. You can leave it in for now. 

Add a comma after the ObjectId's curly bracket and enter whatever fields you'd like your document to have. Don't forget you're writing JSON! All rules apply, including those that allow you to write multiple JSON entries in a single JSON file. You can add multiple documents in the same way; separate each JSON object with a comma, and wrap the entire list of entries in square brackets. 

Add 5 documents, and when you're ready, click the 'Insert' button!

# READ

This one is easy! You can see all of your documents laid out in the white field where the GUI dashboard controls are. If you toggle between collection views however, you begin to unlock a bit of the magic in MongoDB Compass. These buttons can be found to the right of the 'Add Data' button, next to the grey word "VIEW". This becomes more useful the more data we have, as outlined in our next section.

# UPDATE a Document:
 
 Next up, updating! Hover over a document from those you just added. Several options appear, including "Edit document". Select this to edit and update. 
  - What do you notice as you try to update different fields? 
  - How does the _id field react when you try to change it? 
  - What happens when you try to add different fields to different documents? 
  - How do the different entry views change what you learn or how you update documents?

# DELETE a Document:

To delete, simply hover over the document you want to delete and click the furthest right button that appears; a trashcan. Poof!

# AND MORE!

## Tabs:
The tabs at the top of this white field allow us to break down the various pieces of our collection. As a relational database, MongoDB's Compass allows us to pull apart the different relationships our documents have to one another, and begin to analyze patterns. This becomes more useful the larger our collection is! These tabs also allow us to track usage over time, enforce data structures, and take advantage of indexes. Neat!

## FIND:

The search bar above our documents is also very powerful. As such, it needs you to be very specific about what you're looking for. You can't just type in Juniper if you're looking to pull up all documents that contain the word Juniper. If you want to pull all records where the name field equals Juniper, you can do so by calling on the document object using curly brackets and the key: value pair within. 
```js
{ name: "Juniper" }
```

You can expand or minimize your search by revealing advanced search options. Click the 'OPTIONS' drop down in the search bar, to the left of the green 'FIND' button.

You can also glimpse a history of past searches by selecting the clock/arrow button to the right of the 'FIND' and 'RESET' buttons. 

Try it for yourself!


# Add another collection

In the grey sidebar, click on the `test` directory. you will be brought back to the `test` database dashboard, where you can create another collection the same way you made the first. Databases are great; they can hold multiple collections at once! 