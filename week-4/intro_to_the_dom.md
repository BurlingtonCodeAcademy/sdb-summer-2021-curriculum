# The DOM

* stands for Document Object Model
  * "Document" = HTML page
  * "Object Model" = way of describing page elements
    * tags, attributes, styles, text, etc.
* Mostly standard
  * but there are some browser differences
* Core DOM objects
  * Node, Element, Text, Comment, Attr

---

# The BOM

* BOM stands for Browser Object Model
* the global `window` variable has lots of nice properties
    * `window.location`
    * `window.navigator`
    * `window.history`
    * `window.screen`
    * `window.frames`
    * `window.document` -- hey, look! it's the DOM
* And methods
    * `open()`, `close()`
    * `moveTo()`, `sizeTo()`
    * `alert()`, `prompt()`, `confirm()`
    * `setTimeout()`, `setInterval()`

---

# `window` vs. `document`

* `document` is the page
* `window` is the stuff around the page
* Kinda the same, but kinda different

```javascript
window === document
// => false
window.location === document.location
// => true
```

---

# The `document`

In a DOM script, the current page is always available via the *global variable* named `document`.

In addition to providing many useful *functions*, it also provides some *properties*:

|Property|Description|
|---|---|
| `document.URL` | the URL of the current page, in the form of a string. |
| `document.location` | the URL of the current page, in the form of a Location object. |
| `document.location = 'http://example.com'` | causes the browser to visit that web page.|
| `document.title` | the *title* of the document, which appears inside windows and tabs.|
| `document.title = 'the joy of cooking'` | immediately changes the *title* of the document. Some apps use this to display, e.g., a count of unread messages, which the user can then see without switching tabs.|

<https://developer.mozilla.org/en-US/docs/Web/API/Document>

---

# The `window`

* `window.location = "https://google.com"`
  * makes the browser load a new page
* global JS functions are properties of `window`

```javascript
window.x = 7;
x === 7; // true
y = 9;
window.y === 9 // works in reverse too
```

* core JS functions are methods of `window`

```javascript
parseInt('123')         // same
window.parseInt('123')  // thing
```

---

# Locating HTML Elements

* the hard way
  * traverse the document tree using DOM Node methods
* the somewhat easier way
  * `document.getElementsByTagName('p')[0]`
* the easy way
  * `document.getElementById('article')`

---

# Altering HTML Elements

* Target an element through a DOM query and assign it to a variable
* Use the reference to the element to manipulate existing properties
  * Or add entirely new properties

---

# DOM Scripting

"Scripting" is a term used when you're writing programs that don't do much *on their own*; instead scripts usually use other, more advanced programs, or are embedded within them.

"DOM Scripting" means using JavaScript to manipulate the DOM (page elements and contents) inside a web page, either during page load, or in response to user events, like clicking a button or selecting text.

---

# scripts as attributes

This is the simplest way to execute JavaScript inside a Web page.

```html
<button name="button" onclick="alert('Abracadabra!')">
    Magic
</button>
```

Try it out here: <button name="button" onclick="alert('Abracadabra!')">Magic</button>

`onclick` is an *attribute* that contains a *script* that pops up an alert box. Also known as an *event handler*.

(We will discuss several other ways to attach event handlers later.)

---

# the script tag (no src)

Without a `src` attribute, it defines a script and *immediately executes* its code:

```html
<script>
  var message = "Shazam!"
  alert(message)
</script>
```

---

# the script tag (src)

With a `src` attribute, it *loads code from a separate file*, and and *immediately executes* it:

```html
<script src="tictactoe.js"></script>
```

This code expects a file named `tictactoe.js` to *exist on the server* in the same directory as the HTML file.

The `script` tag may appear in the `head` or in the `body`. Scripts are executed in top-to-bottom order.

> HINT: to be sure that your code executes after the page has been fully loaded, put your `<script>` tags at the *bottom* of the `<body>` section.

---

# DOM Queries

To access the elements on our page, and bring them into JavaScript we can use a special set of methods on the `document` object called DOM queries

* `getElementsByTagName()`
* `getElementsByClassName()`
* `getElementById()`
* `querySelector()`
* `querySelectorAll()`

---

# Finding an Element by ID

If an element has an `id` attribute, you can get a *pointer* to that element with a single line of code:

```js
let element = document.getElementById(id);
```

Once you have a pointer to that element, you can manipulate it further. You can also log it to the console for further inspection using:

```js
console.log(element)
```

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById>

---

# Finding an Element by CSS Selector

```js
let element = document.querySelector('main div.preview > p')
```

This returns the first Element within the document that matches the specified selector (in this case, the first `<p>` that is a direct child of any `<div class='preview'>` that is in the `main` section).

<https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector>

---

# Using an Element

Once you find an element (using `getElementById` or any other way), you can start attaching behavior, or modifying its attributes.

```js
let header = document.getElementById('header')
let text = header.textContent
```

There is also a property called `innerText` but it's confusing and implemented differently in different browsers.

<https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent>

---

# Adding HTML

* brute force (raw HTML strings)

```javascript
document.write("<p id='message'>hi</p>");  // :-( this freaks out Firebug Console

var message = document.getElementById('message');
message.innerHTML = "<b>bye</b>!";
```

* programmatically with JS

```js

let target = document.getElementById('someElement')

let paragraph = document.createElement('p')
paragraph.textContent = "I’ve seen things you people wouldn’t believe. Attack ships on fire off the shoulder of Orion. I watched C-beams glitter in the dark near the Tannhauser gate. All those moments will be lost in time, like tears in rain."

target.appendChild(paragraph)
```

---

# Code Along: Update an Element

<iframe height="600" style="width: 100%;" scrolling="no" title="DOM-scripting-lab-1" src="https://codepen.io/burlingtoncodeacademy/embed/preview/gOpMvgr?height=265&theme-id=light&default-tab=html,result&editable=true" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/gOpMvgr'>DOM-scripting-lab-1</a> by Joshua Burke
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

---

# Nodes vs Elements

In the DOM, the term "node" means *almost any* item that you can find in the document tree.

When you're hunting for a function or property, sometimes it's on a Node, and sometimes it's on an Element. Make sure to check *both* of these documentation pages:

  * <https://developer.mozilla.org/en-US/docs/Web/API/Node>
  * <https://developer.mozilla.org/en-US/docs/Web/API/Element>

For instance, `attributes` is a property of an Element, but `childNodes` is a property of a Node.

---

# Other Node Types

An element is a particular type of node, and it's the most common, but beware, these are also nodes...

* Document, Element, Text, Comment, CDATASection, ProcessingInstruction, DocumentFragment, DocumentType, Notation, Entity, EntityReference

...and all of them have their own properties that are *not* part of the basic Node set.

> Also, this sense of "node" is **completely different** from the "node" in NodeJS. :-(

---

# Finding many elements

In addition to getting a *single* element by its `id` or a CSS selector, you can also ask the document to give *all* elements that match a certain criterion.

```js
let elements = document.getElementsByClassName('profile-picture')
```

> by *CSS Class* name

```js
let elements = document.getElementsByTagName('h2')
```

> by *Element* name

```js
let elements = document.querySelectorAll('h2.preview > p')
```

> by *CSS Selector* expression

These return *collection* objects, so you must write more code to get the actual element objects, or to check the collection's length.

---

# HTML Collections

DOM queries that can target multiple elements always return a data structure called an *HTML Collection*. This is an array like object, but it *is not an array*. It will be an ordered list with a `length` property, but has no methods attached to it.

We can turn it into a real array several different ways

* `Array.from(collection)`
* Iterate over it with a `for...of` loop, and push each value to an empty array
* use the *spread* operator `[...collection]`

Please not that I am using `collection` as a variable name to represent the HTML collection. The word "collection" has no special meaning in JavaScript.
