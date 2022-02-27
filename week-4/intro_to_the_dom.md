# The DOM

- Document Object Model
  - Document - HTML page
  - Object - HTML elements and comments that the browser calls **Nodes** (not like node.js)
  - Model - Arranging them to make sense
- The DOM is in the browser
  - Different browsers mean different DOMs.

> We can access the DOM in JavaScript with the built-in `document` object.

---

# The BOM

- BOM stands for Browser Object Model
- the global `window` variable has lots of nice properties
  - `window.location`
  - `window.navigator`
  - `window.history`
  - `window.document` -- The DOM exists in the Window
- And methods
  - `open()`, `close()`
  - `moveTo()`, `sizeTo()`
  - `alert()`, `prompt()`, `confirm()`
  - `setTimeout()`, `setInterval()`

---

## `window` vs. `document`

- `document` is the page
- `window` is the browser itself

---

## The `document`

The current page is always available via the _global variable_ named `document`.

In addition to providing many useful _functions_, it also provides some _properties_:

| Property                                         | Description                                                    |
| ------------------------------------------------ | -------------------------------------------------------------- |
| `document.URL`                                   | The URL of the current page, as a String.                      |
| `document.location`                              | The URL of the current page, in the form of a Location object. |
| `document.location = 'http://example.com'`       | Causes the browser to go that web page.                        |
| `document.title`                                 | The _title_ of the document/webpage.                           |
| `document.title = 'Facebook - 1 unread message'` | Changes the _title_ of the document.                           |

<https://developer.mozilla.org/en-US/docs/Web/API/Document>

---

## The `window`

All of the global "built-in" functions and variables you've used and made thus far actually exist in the `window` object.

```javascript
window.x = 7;
x === 7; // true
y = 9;
window.y === 9; // works in reverse too

parseInt("123"); // same
window.parseInt("123"); // thing
```

---

## Using JS to Get Elements from the DOM

```js
let allTheParagraphs = document.getElementsByTagName("p");
let firstParagraph = allTheParagraphs[0];

let article = document.getElementById("article");

let elementsWithButtonClass = document.querySelectorAll(".button");

let firstElementWithButtonClass = document.querySelector(".button");
```

---

## Practice

Take a few minutes to practice grabbing and manipulating DOM elements.

<https://replit.com/team/education-team/dom-manipulation-practice>

We will discuss parts of this in more detail in future slides.

---

## Including JavaScript Files in your HTML

```html
<script>
  var message = "Shazam!";
  alert(message);
</script>

<script src="script.js">
```

The `script` tag may appear in the `head` or in the `body`. Scripts are executed in top-to-bottom order.

> HINT: to be sure that your code executes after the page has been fully loaded, put your `<script>` tags at the _bottom_ of the `<body>` section.

---

## DOM Queries

To access the elements on our page, and bring them into JavaScript we can use a special set of methods on the `document` object called DOM queries

- `getElementsByTagName()`
- `getElementsByClassName()`
- `getElementById()`
- `querySelector()`
- `querySelectorAll()`

---

## Finding an Element by ID

If an element has an `id` attribute, you can get a variable to point to that element with a single line of code:

```js
let element = document.getElementById(id);

console.log(element);
```

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById>

---

## Finding an Element by CSS Selector

You can select items from the DOM the same way you would in CSS to apply styles.

```js
let element = document.querySelector("main div.preview > p");
```

This returns the first `<p>` that is a direct child of any `<div class='preview'>` that is in `<main>`.

<https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector>

---

## Using an Element

Once you find an element (using `getElementById` or any other way), you can start attaching behavior, or modifying its attributes.

```js
let header = document.getElementById("header");
let text = header.textContent;
```

There is also a property called `innerText` but it's confusing and implemented differently in different browsers.

<https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent>

---

## Adding HTML

```js
document.write("<p id='message'>hi</p>");

var message = document.getElementById("message");
message.innerHTML = "<b>bye</b>!";
```

Preferred:

```js
let target = document.getElementById("someElement");

let paragraph = document.createElement("p");
paragraph.textContent =
  “If you cannot solve a problem, then there is an easier problem you can solve: find it. 
  - George Polya” ;

target.appendChild(paragraph);
```

---

## Nodes vs Elements

The Element class inherits from the Node class, but that does not mean they are identical.

- <https://developer.mozilla.org/en-US/docs/Web/API/Node>
- <https://developer.mozilla.org/en-US/docs/Web/API/Element>

For instance, `attributes` is a property of an Element, but `childNodes` is a property of a Node.

---

## Other Node Types

Elements are the most common Nodes; here are some others kinds of Nodes:

- Document, Element, Text, Comment, CDATASection, ProcessingInstruction, DocumentFragment, DocumentType, Notation, Entity, EntityReference

All of them have their own properties that are specific to them and not part of the general Node class.

---

## Finding many elements

In addition to getting a _single_ element by its `id` or a CSS selector, you can also ask the document to give _all_ elements that match a certain criterion.

by _CSS Class_ name

```js
let elements = document.getElementsByClassName("profile-picture");
```

by _Element_ name

```js
let elements = document.getElementsByTagName("h2");
```

by _CSS Selector_ expression

```js
let elements = document.querySelectorAll("h2.preview > p");
```

---

## HTML Collections

DOM queries that can target multiple elements always return a data structure called an _HTML Collection_. This is an array like object, but it _is not an array_. It will be an ordered list with a `length` property, but has no methods attached to it.

We can turn it into an array to be able to use Array methods with it.

- `Array.from(collection)`
- use the _spread_ operator `[...collection]`

> `collection` is a pretend variable name here used to represent the HTML collection. The word "collection" has no special meaning in JavaScript.
