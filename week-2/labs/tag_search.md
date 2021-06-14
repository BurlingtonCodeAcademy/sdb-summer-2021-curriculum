# Tag Search

## Welcome!

Tags are a common way of searching data. In this lab we will be building a program that can filter an array of books to return a list of books with certain tags attached to them.

## Creating the Books

For this lab we'll be using objects to represent our books. This is a very common way for JavaScript to represent query results from something like a database, or as a response to a user typing into a search bar. We'll be covering objects in more depth later this week, but for now here's what you need to know about them:

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
    title: "A Wizard of Earthsea",
    tags:['fantasy', 'ursula k. le guin']
  },
  {
    title: "Thing Explainer",
    tags:["science", "technology", "humor", "randal munro"]
  },
  {
    title: "The Fellowship of the Ring",
    tags:["fantasy", "jrr tolkien"]
  },
  {
    title: "A Brief History of Time",
    tags:["history", "science", "stephen hawking"]
  },
  {
    title: "The Great Fairy Tale Tradition",
    tags:["fairy tale", "history", "jack zipes"]
  },
  {
    title: "The Hitchhiker's Guide to the Galaxy",
    tags:["science fiction", "humor", "douglas adams"]
  },
  {
    title: "The Silmarillion",
    tags:["fantasy", "mythology", "jrr tolkien"]
  },
  {
    title: "Eloquent JavaScript",
    tags:["programming", "technology", "marijn haverbeke"]
  }
];
```

To access the title of the first book in the array we could use *square bracket notation* to access the first object in the array, and then *dot notation* to access the `title` property.

```js
let firstBook = results[0];

let title = firstBook.title;
```

We could also do this all on one line, like so:

```js
let firstTitle = results[0].title;
```

And we can access the `tags` array in the same manner

```js
let firstBook = results[0];

let tags = firstBook.tags;
```

## Define the Function

Create a function that will take a single argument. The argument will represent the tag you are searching for as a *string*, and the function will return a new array of each book with the matching tag. I'm going to refer to the function as `search` from here on out.

## Iterating Over an Array

Our `search` function will need to iterate over an array, and filter out the results with matching tags. Conveniently enough there's a [`.filter` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) that can do just that!

## Accessing Each Item

To create the check for our `.filter` we need to access the properties on the current item, and see if our `tags` array contains our search term. We can get our `tags` from inside our filter iterator by accessing the `tags` array on the current item: `item.tags`

Once we have the `tags` array we can call the `.includes` method on it passing in our search term as the argument. This should work nicely as the check for `.filter`

## Try it Out

Given our starting array, if we called `search` and passed in `"fantasy"` as the argument we should see the objects for The Silmarillion, The Fellowship of the Ring, and A Wizard of Earthsea:

```js
{
  title: "A Wizard of Earthsea"
  tags:['fantasy', 'ursula k. le guin']
},
{
  title: "The Fellowship of the Ring"
  tags:["fantasy", "jrr tolkien"]
},
{
  title: "The Silmarillion"
  tags:["fantasy", "mythology", "jrr tolkien"]
}
```

Call `search` passing in a tag of your choice, and run the program to see your results.

## Going Further

- How could we modify the program to only print the titles of our search results?
- How could we make this program interactive, so that when you run it in the command line and it would allow you to type in your search term?
- How could we filter by multiple tags at once?
