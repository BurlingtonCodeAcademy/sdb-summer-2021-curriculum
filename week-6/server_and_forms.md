# Forms contain inputs

a `<form>` is an HTML element that contains input elements

  * when the user enters data into these input elements
  * and clicks the "Submit" button
  * then the browser will wrap up all those values and send it to the server

[MDN: form](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)

---

# Form Example

```html
<form method='post'>
  Name: <input type='text' name='name' value='Alice'>
  <br />
  Password: <input type='password' name='password'>
  <br />
  <input type='submit'>
</form>
```


<form method='post'>
  Name: <input type='text' name='name' value='Alice' />
  <br />
  Password: <input type='password' name='password' />
  <br />
  <input type='submit' />
</form>

---

# Forms are semantic

* a form wraps *input* elements for submission
  * but may also *include* or *be included within* other styled elements
* most of the time your `<form>` element will correspond to a block element (viz. the border of the form)
  * but by default `<form>` is an *inline* element
  * and instead of making it a block element, it's usually better to wrap it in a `div` 
  * and apply styles to the wrapper and leave the `form` alone

---

# Form attributes

```html
<form method='get' action='/login'>
```

* `method` corresponds to the *first word* in the HTTP protocol
  * "GET" is the standard (default) method; there are also POST, PUT, HEAD, DELETE, [etc.](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)
* `action` is the server path to submit the form to
  * if it's blank then it uses the *same path as the current page* (which is usually not what you want)

---

# Form Methods: GET vs. POST

* `GET` means "return me a page (based on these parameters)"
* `POST` means "take these parameters (and return me a page)"

Basically, `GET` is for *reading* and `POST` is for *writing*

but that distinction is often blurry

Also,

  * `GET` sends all parameters via the *request URL*
  * `POST` sends some or all parameters via the *request body*

---

# Form elements

```html
<form method='GET' action='/search'>
  <label>Search by Author: <input type="search" name="author"></label>
  <input type='submit' value='Search'>
</form>
```

* `<label>` marks some text as belonging to a certain input element
* `<input name='q' type='search'>` is a text field
  * (that removes line breaks and may look different)
* `<input type='submit' value='Search'>` is a **button** whose **label** is the string "Search"
  * (yes, the names are confusing; the submit button goes way back to HTML 1.0)

There are many more types of form elements (or "widgets") that let the user enter data in a wide variety of formats.

---

# Form submission: how does it work?

![client-server illustration](https://developer.mozilla.org/files/4291/client-server.png)

1. The user enters some values into the form elements
2. **Either**...
  * the user clicks "Submit"
  * or the user presses <kbd>Enter</kbd> in a text field
3. The client sends an HTTP request
  * including query parameters if it has a `method` of `"get"`

---

# Forms as Input

Forms are a great way to accept user input in your webpages. The simplest way to handle user input is to create a form with an `<input type="text" />` element, and an `<input type="submit" />` element.

This can be used to set up anything from providing information to the page, to simple login, to full database operations

If we do not intercept the form with JavaScript on the front end, then our form data gets sent to the server where we can deal with it in a more secure environment.

If we send the form data via a `POST` request it further hides the data by sending it over in the request's `body` property rather than through the URL

---

# Reading Request Bodies in Express

To read a post request's body on your express server you will need to use some middleware to transform it into a format you can interact with. Luckily express comes with some build in middleware. `express.urlencoded()` used as middleware allows us to transform a POST request's `body` into a JavaScript object.

Middleware can be set up in an `app.use` method, before you set up your routes, or directly inline in the desired route.

```js
app.use(express.urlencoded())

app.post("/some/path", (req, res) => {
  console.log(req.body)
})
```

---

# References

<https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form> - docs

<https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms> - guide
