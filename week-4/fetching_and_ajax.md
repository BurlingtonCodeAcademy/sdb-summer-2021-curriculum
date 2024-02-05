# AJAX

AJAX stands for **Asynchronous JavaScript And XML**.

1. Request data from an external source
2. Parse the data returned by the request
3. Load that data into the page **without a refresh**
4. Data can be any formats, most common:
   - XML
   - JSON
   - HTML fragment (not an entire page)

---

## AJAX Examples

- Load the comments on an article _later_, so the rest of the page is usable sooner
- Once a minute, check for any _new_ comments and display them too
- Load today's weather forecast from DarkSky.net, and update it every hour
- Load an ad from a _different web server_ and switch ads every few minutes
- Dynamically display _search results_ as the user types their query
- Infinite scrolling like Pinterest or Twitter

---

## Advantages

- Page components can be loaded individually
- New data can be loaded asynchronously
- User interacts with the page and sees results almost immediately
  - or at least more quickly than a full page reload

---

## Disadvantages

- JavaScript must be enabled
- Adds complexity to JavaScript applications
- Without refreshes the page state can get bloated
  - Memory leaks become a bigger problem in longer-lived apps
- Screen-readers cannot read the whole page at once #a11y
- Reloading the page can show completely different content
  - Bookmarking and link sharing no longer "just work"

---

## What Makes Ajax Possible?

Ajax is not a single technology. It is really several technologies, each flourishing in its own right, coming together in powerful new ways. Ajax incorporates:

- Standards-based presentation using **HTML and CSS**
- Dynamic display and interaction using the Document Object Model
- Data interchange and manipulation using **JSON**
- Asynchronous data retrieval using **Fetch**
- JavaScript binding everything together

> This collaboration allows web applications to meaniningfully compete with desktop applications.

---

## Fetching Data

- JavaScript has a built-in tool called **fetch** that allows us to make `GET` requests to a server
- A **GET request** is when we ask another computer for information or files
- Every time you visit a site, you make a `GET` request to the server
- Make a `GET` request to this address to see the response:
  - <https://jsonplaceholder.typicode.com/posts/1>

---

## Fetching Remote Data

How do we get the information from that request into a JavaScript file?

Ask for it:

```js
let response = await fetch(`https://jsonplaceholder.typicode.com/posts/1`);
```

Process it as text:

```js
let text = await response.text();
```

**Or** process it as JSON (much more common):

```js
let json = await response.json();
```

---

## Fetching Local Data

We can use a relative (partial) URL for the data source as well:

```js
let response = await fetch("/some-blog-post.md");

let blogText = response.text();
```

---

## Catching Errors

When there is a chance of an error being `thrown`, we want to `catch` it.

```js
try {
  let response = await fetch(
    "https://jsonplaceholder.typicode.com/posts/NO-POST-AVAILABLE-HERE"
  );
  let user = await response.json();
  if (!response.ok) {
    throw Error("I AM NOT OK");
  }
} catch (errorFromResponse) {
  // Any Errors, from you or others, in the try block will trigger this catch block
  alert(errorFromResponse);
}
```
---

## JSON

- JSON is JavaScript Object Notation.
- It's the most common format for sending information via requests.
- It's nearly identical to a JavaScript Object and works similarly.
- It only holds data -- no comments or functions

We cover JSON in more detail in Week 6.

---

## JSON Example

```js
{
  "userId": 1,
  "id": 1,
  "title": "My most amazing post",
  "body": "This is my first post, isn't it great. Maybe I'll write some more."
}
```

You can use a [JSON viewing tool](http://jsonviewer.stack.hu) to more easily analyze JSON data visually.

---

## Parsing & Producing JSON

The Fetch API converts text into JSON for you if you call `response.json()`

but if you want to do it yourself...

`JSON.parse` converts a string into an object:

```javascript
let data = JSON.parse(string);
```

---

## Parsing JSON Example

```js
let myText = "{ 'data': 'some data goes here' }";
let myObject = JSON.parse(myText);
console.log(myObject);
```
