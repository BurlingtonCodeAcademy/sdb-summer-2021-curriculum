# Tag Search

## Welcome!

Tags are a common way of searching data. In this lab we will be building a program that can filter an array of books to return a list of books with certain tags attached to them.

## Creating the Books

For this lab we'll be using objects to represent our books. This is a very common way for JavaSCript to represent query results from something like a database, or as a response to a user typing into a search bar. We'll be covering objects in more depth later this week, but for now here's what you need to know about them:

- Objects are a way of creating an `unordered` list in JavaScript
- Like arrays, objects can hold any type of data
- Objects are defined with curly braces `{}`
- **But** to access the value of the data you use *keys* that are defined on the object rather than index numbers
  - The key-value pair is called a *property* of the object
- To access the value of a property you can use *dot notation*

Let's create our `results` array, and see how we can access the properties on the objects it contains. We'll start with 8 results, each with a `title` and a `tags` property. Tags will be an array with strings representing the genre(s) of the book, and the author's name.

```js
let results = [
  {
    title: "A Wizard of Earthsea"
    tags:['fantasy', 'ursula k. le guin']
  },
  {
    title: "Thing Explainer"
    tags:["science", "technology", "humor", "randal munro"]
  },
  {
    title: "The Fellowship of the Ring"
    tags:["fantasy", "jrr tolkien"]
  },
  {
    title: "A Brief History of Time"
    tags:["history", "science", "stephen hawking"]
  },
  {
    title: "The Great Fairy Tale Tradition"
    tags:["fairy tale", "history", "jack zipes"]
  },
  {
    title: "The Hitchhiker's Guide to the Galaxy"
    tags:["science fiction", "humor", "douglas adams"]
  },
  {
    title: "The Silmarillion"
    tags:["fantasy", "mythology", "jrr tolkien"]
  },
  {
    title: "Eloquent JavaScript"
    tags:["programming", "technology", "marijn haverbeke"]
  }
]
```

To access the title of the first book in the array we could use *square bracket notation* to access the first object in the array, and then *dot notation* to access the `title` property.

```js
let firstBook = results[0]

let title = firstBook.title
```

We could also do this all on one line, like so:

```js
let firstTitle = results[0].title
```

And we can access the `tags` array in the same manner

```js
let firstBook = results[0]

let tags = firstBook.tags
```

## Define the Function

## Iterating Over an Array

## Accessing Each Item

## Filtering the Results

## Test it Out

## Adding Interactivity