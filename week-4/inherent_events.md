# Built-In Events

Up until now, we've manually added event listeners to enable interactivity.

However, some tags expect to be interactive:

- buttons
- anchors
- forms

---

## Buttons

`<button>` elements listen for `onclick` events.

This is how the browser knows to change the button's styling to appear like it's being pushed down when someone clicks.

---

## Anchors

- `<a>` elements listen for `onclick` events so it knows when to send you to the linked location.

> Note: We can link to other pages or other spots within the same page.

---

## Internal Anchors

- We've used links that send you to different pages, but what about farther down the same page?
- We can use the `id` attribute of elements to use `<a>` to send us to a different part _of the same page_.
- We use the `id selector #` in the `href` attribute to do this.

```html
<a href="#pizza">🍕</a>
<a href="#burger">🍔</a>

<h2 id="pizza">Clicking 🍕 sends you here.</h2>

<p>Content in between gets skipped, since that's the point.</p>

<h2 id="things">Clicking 🍔sends you here.</h2>
```

---

## Forms

`<form>` tags listen for `onsubmit` events to know when to send your form input somewhere.

`onsubmit` events trigger the following behaviors:

- The browser redirects to the URL from the `action` attribute.
  - `<form action="https://example.com">`
  - If no `action` attribute exists, it refreshes the page.
- It attaches a **query string** to the `action` URL

  - The key/value pairs being the `name` of each input, and the `value` for that input.

  > [Query strings allow you to save information like you would in an object but in a string instead.](https://en.wikipedia.org/wiki/Query_string)

---

## Forms Cont.

`<form>` tags are used to group `<input>` tags together.

```html
<form>
  <label>
    First Name:
    <input type="text" name="first-name" />
  </label>
</form>
```

- The browser listens for typing in these inputs.
- When `onsubmit` is triggered, the browser collects the data from these `<input>`s.

[MDN: form](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)<br/>
[Accessible form builder](https://accessify.com/tools-and-wizards/accessibility-tools/quick-form-builder/)

---

## Forms and HTTP

You may have noticed `method="POST"` in the previous example.

**HTTP** is HyperText Transfer _Protocol_, meaning the rules we follow when we transfer text data.

- `method` is what we are doing witht the data
  - GET - asking to read data
  - POST - saving data
  - PUT - editing data
  - DELETE - deleting data
- `action` is the URL we submit data to

Combined, we can send data to other sites and tell those sites what we want them to do with said data.

---

## Using JavaScript with Forms

- We can use JavaScript to add _submit handler_ function.
- This function will be invoked when the `onsubmit` event fires.
  - i.e. the user clicks "Submit"
- The `Event` and its data is passed to your _submit handler_ function as an argument _before_ being sent to a server.
- This lets you modify data, execute other code, or _cancel_ the submission.
- When using JavaScript with a form, you may want to stop the automatic refresh behavior by doing one of these:
  - `<form href="#">` in your HTML
  - `event.preventDefault();` as the first line in your _submit handler_ block.

---

## Form submission: how does it work?

1. The user enters some values into the form elements
2. The form begins to submit as a result of one of these behaviors:

- clicking "Submit"
- pressing <kbd>Enter</kbd> while in a text field
- or JavaScript calls `form.submit()` on the form DOM element

3. The user's computer (**client**) sends an HTTP request

- The data from the form is included as a **query string** like `?item=apple&submit=Search`

---
