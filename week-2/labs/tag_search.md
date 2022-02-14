# Tag Search

## Objective

Tags are a common way of searching for data. In this lab we will be building a program that can filter an Array of books to a sub-Array that match a search term based on the tags each book contains.

## Learning

In this lab, we will practice making an `Array` of `Objects`, writing a function that can iterate over that `Array`.

- `Arrays`
- `Objects`
- Array methods
- key-value pairs

### Links

- [MDN Arrays](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Arrays)

-[MDN Objects](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)

## Achieving

In this lab, we will achieve a piece of software that can filter an array of books to return a list of books with certain tags attached to them.

Your work will result in:

- A `tag-search.js` file
- `library` array
- `search` function

## Procedure

### Create the `tag-search.js` file

- [ ]  Create a new file named `tag-search.js` and open it in your editor.

### Create the `library` array variable

- [ ] Initialize a variable named `library` which will serve as our collection of books.
- [ ] Set the value of the `library` variable equal to an empty array.
- [ ] Within this array create four(4) separate objects with the keys `title` and `tags`.
- This should look something like the following:

```js
let library = [
  {
    title: "A Game of Thrones",
    tags:['fantasy', 'george r.r. martin']
  },
  {
    title: "Eloquent JavaScript",
    tags:["technology", "programming", "marijn haverbeke"]
  },
  {
    title: "The Fellowship of the Ring",
    tags:["fantasy", "jrr tolkien"]
  },
  {
    title: "The Return of the King",
    tags:["fantasy", "jrr tolkien"]
  }
] 
```

### Create the `search` function

- [ ] Create a function named `search` that will accept a `tag` as its only argument.
- [ ] Within the `search` code block, return the result of using the [`.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) method on your `library` array.
- [ ] Within the call to `.filter()` pass a function as an argument that accepts the current book as an argument. `.filter(function (someBook) { ... })`.
- [ ] Within the callback function, compare the current book's `.tags` property to the search term. Consider using the [`.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) method to do this.
- [ ] Remember to `return` the current book if its tags match the search term.

### Invoke the `search` function

- [ ] Use the `search` function by invoking the function, while passing in a tag to search for as a string.

## Review

In this lab, we made a piece of software that can filter an array of books to return a list of books based on certain tags that are attached to them.

The software should:

- Call the `search` function, taking in a string as an argument.
- Filter over our `library` array, checking to see if the `tags` array includes the string we passed into `search`.
- Return the books with the included tags.

## Going Further

- How could we modify the program to return only the `title` of the matching books?
- How could we make this program interactive, so that when you run it in the command line and it would allow you to type in your search term?
- How could we filter by multiple tags at once?
- How could we filter by tags and the book's author?
