# Inherent Events

While the main way of making a page interactive is to manually add event listeners to elements, some elements have inherent behavior for certain events.

Most notably:

* buttons
* anchor tags
* forms

---

# Buttons

`<button>` elements have some inherent `onclick` behavior.

It's fairly unobtrusive and just alters the button's styles so it looks like it get pressed in.

---

# Anchors

* Anchor tags have an inherent `onclick` property to help with their main purpose; linking to other locations.
* *internal anchors* are linked to `id` properties on the page
* when linking to an *inner anchor*, use the # character to distinguish *external anchors* from *internal anchors*)

```html
<a href='#stuff'>here is my stuff</a>
<a href='#things'>here are my things</a>
...

<h2 id='stuff'>My Stuff</h2>
...
<h2 id='things'>My Things</h2>
```

---

# Anchor links

* Anchor tags create links to a linkable location
    * Within the same page, using an `#someId` selector
    * Other pages within the site, using relative paths `href="/somePage.html"`
    * External webpages, using a full URL `href="https://www.example.com"`

```html
<a href="/about">About Me</a>
```

---

# Forms `onsubmit`

When the submit button on a form is clicked the form element itself emits a "submit" event which does several things:

* It redirects to the URL set as the `action` property on the form
  * If no `action` property exists it will refresh the current page
* It attaches a query parameter to your URL
  * The key/value pairs being the `name` of each input, and the value for that input.

---

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

# Intercepting forms with JavaScript

* your JavaScript code can add a *submit event handler*
  * also known as "onsubmit"
* this function will be called after the user clicks "Submit"
  * but before the data is sent to the server
* this lets you *modify* the data sent to the server, or execute code *before* sending the data to the server, or just *cancel* the server call altogether
* if you intend a form to only be used by JavaScript, do one or both of these: 
  * `<form href='#'>` in your HTML
  * `event.preventDefault();` in your JS event handler

---

# Form submission: how does it work?

![client-server illustration](https://developer.mozilla.org/files/4291/client-server.png)

1. The user enters some values into the form elements
2. **Either**...
  * the user clicks "Submit"
  * or the user presses <kbd>Enter</kbd> in a text field
  * or JavaScript calls `form.submit()` on the form DOM element
3. The client sends an HTTP request
  * including parameters like `?item=apple&submit=Search`

---

# Forms as Input

Forms are a great way to accept user input in your webpages. The simplest way to handle user input is to create a form with an `<input type="text" />` element, and an `<input type="submit" />` element.

When the form is submitted you use JavaScript to read the value of the text field, and do whatever manipulations, or actions you need to do based on that input.
