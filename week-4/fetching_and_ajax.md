# AJAX

AJAX enables

  * loading data into your web page from a web server...
  * ... **after** the page initially loads!

---

# AJAX Examples

  * Load the comments on an article *later*, so the rest of the page is usable sooner
  * Once a minute, check for any *new* comments and display them too
  * Load today's weather forecast from DarkSky.net, and update it every hour
  * Load an ad from a *different web server* and switch ads every few minutes
  * Dynamically display *search results* as the user types their query
  * Infinite scrolling like Pinterest or Twitter

---

# AJAX Definition

**Asynchronous JavaScript And XML**

1.  Request data from an external source
2.  Parse the data returned by the request
3.  Load that data into the page **without a refresh**
4.  Data can be any formats, most common:
    * XML
    * JSON
    * HTML fragment (not an entire page)

---

## Advantages

* Page components can be loaded individually
* New data can be loaded asynchronously
* User interacts with the page and sees results almost immediately
  * or at least more quickly than a full page reload

---

## Disadvantages

* JavaScript must be enabled
* Adds complexity to JavaScript applications
* Without refreshes the page state can get bloated
  * Memory leaks become a bigger problem in longer-lived apps
* Screen-readers cannot read the whole page at once #a11y
* Reloading the page can show completely different content
  * Bookmarking and link sharing no longer "just work"

---

# AJAX History

* (1998) First implemented by Microsoft for use in Outlook email web client
* (1999-2003) Several other browsers copied Microsoft for compatibility
* (2004) Google used XMLHttpRequest for loading data in Gmail and Google Maps
* (2005) AJAX Name coined by Jesse James Garrett [0]

[0] http://adaptivepath.org/ideas/ajax-new-approach-web-applications/

---

# Jesse James Garrett Quote

(corrected for modern use)

Ajax isn’t a technology. It’s really several technologies, each flourishing in its own right, coming together in powerful new ways. Ajax incorporates:

* standards-based presentation using ~~XHTML~~ **HTML and CSS**
* dynamic display and interaction using the Document Object Model
* data interchange and manipulation using ~~XML and XSLT~~ **JSON**
* asynchronous data retrieval using ~~XMLHttpRequest~~ **Fetch**
* and JavaScript binding everything together.

**This was the moment that people realized web applications could be a competitor to desktop applications, and could run on every computer in the world.**

---

# XMLHttpRequest (Old Way)

* The XHR interface is quite complicated
* You must construct an XHR object, set some properties, then call `open()`, then call `send()`
* Your response handler must track the `readyState` property of the request and error checking is cumbersome

Luckily, with the introduction of the `fetch` function we no longer need to use this method!

---

# Browser Fetch API - Plain Text

> The Fetch interface is concise

* Please type this URL into the address bar of your browser

<https://jsonplaceholder.typicode.com/posts/1>

---

# Bringing it Into JS

To access that data in javascript we could do something like this:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(function(response) {
    console.log(response.status);
    return response.text();       // body is not quite ready yet
  })
  .then(function(text) {
    console.log(text);            // now the body is ready
  });
```

* `fetch()` takes at least one argument, the URL of the resource to fetch
* `fetch` returns a [Promise](https://developer.mozilla.org/en-US/docs/Glossary/Promise), to which you add a series of *callbacks* using the `then` method
* `fetch` then calls the server, *just like you did* in the address bar above
* Later on, after the response is received, `fetch` calls your callbacks in order
* The server passes the [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response) into the **first** callback function

---

# Why Two Thens?

* The first `then` gets called once the *HTTP headers* of the response are available
* but the body might not be ready yet
* so from the first response, you call `response.text()`, which returns **another promise**
  * you immediately return that new promise from the callback
* the second `then` gets called after the entire body has been received
  * its parameter is a string containing the full text

---

# Browse Fetch API - JSON

```javascript
let postNumber = 1;
fetch('https://jsonplaceholder.typicode.com/posts/' + postNumber)
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```

* `response.json()` is an alternative to `response.text()`
* The server passes the Response from the server into the **first** callback function
  * `response.json` parses the body of the response as JSON and returns real JavaScript objects
* it returns a *promise to parse* the body as JSON
* the second `then` receives a *proper JavaScript Object* which is the result of calling `JSON.parse()` on the body

---

# Browser Fetch API - Local

If you want to request data from a **local** webserver, use a partial URL 

```javascript
fetch('/city-market.md')
  .then(function(response) {
    return response.text();
  })
  .then(function(myText) {
    console.log(myText);
  });
```

* The first `then` function happens to return `response.text()` because it is a Markdown file
* If it were JSON then we'd use `response.json()`

---

# Browser Fetch API - Errors

* The system will raise errors as exceptions by default
* If you want to handle errors catch them like shown below
* Use `.catch(function(error) { do_something_here })`
* Server responses like "404 Not Found" are **not** considered errors by Fetch; only network errors trigger a `catch`

---

```javascript

fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(function(response) {
    if (!response.ok) {
      console.log('HTTP error: ' + response.status);
    } else {
      return response.json();
    }
  })
  .then(function(json) {
    console.log(json);
  })
  .catch(function(error) {
    console.error('Network error:\n', error);
  });
```

---

# JSON (JavaScript Object Notation)

For now what you need to know about JSON i that it's one of the most common ways of passing data around on the internet, and is essentially just a JavaScript object.

See a more comprehensive JSON lesson here: [JSON lesson](/lessons/sixth-week/json-data)

---

# Example

```js
{"userId": 1,
  "id": 1,
  "title": "My most amazing post",
  "body": "This is my first post, isn't it great. Maybe I'll write some more."
}
```

---

# JSON Rules

* No comments
* No functions
* Only data is allowed
  * Objects (Hashes), Arrays, Numbers, Booleans, Strings

---

# Parsing & Producing JSON

The Fetch API converts text into JSON for you if you call `response.json()`

but if you want to do it yourself...

`JSON.parse` converts a string into an object:

```javascript
let data = JSON.parse(string)
```

---

# Parsing JSON Example

So this would work fine:

```javascript
fetch('/city-market.json')
  .then(function(response) {
    return response.text();
  })
  .then(function(myText) {
    let myObject = JSON.parse(myText);
    console.log(myObject);
  });
```