# Event Listeners

Back in the first week we touched briefly on event listeners as a way of handeling user input. Event listeners are the main way of making a webpage interactive.

While all HTML elements have properties that listen for certain events, such as `onclick` or `onsubmit` it is very common to attach event listeners using the `addEventListener` method

`addEventListener` is a method that takes two arguments. The first is a *string* representing the name of the event, and the second is a *function definition* called an *event handler*

---

# Events as functions

In JavaScript, *event handlers* are *callback functions*.

The classic example of an event handler is "onclick", i.e. "please call this function when the user clicks this button".

To attach an event handler,

1) Find the element, e.g.

```js
let button = document.getElementById('magic');
```

2) Attach the callback, like this:

```js
button.addEventListener('click', () => { alert('Abracadabra!') });
```

> NOTE: using the "fat arrow" for event handlers is a **very good idea** since fat arrows will restore the `this` variable to point to the same object as when the listener was added.

<https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener>

---

# Code Along: Update Element on Click

<iframe height="600" style="width: 100%;" scrolling="no" title="DOM-scripting-lab-2" src="https://codepen.io/burlingtoncodeacademy/embed/preview/vYOKdJO?height=265&theme-id=light&default-tab=html,result&editable=true" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/vYOKdJO'>DOM-scripting-lab-2</a> by Joshua Burke
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

---

# Events by Reference

If you have already defined an event handler function, you can attach it by reference, like this:

```html
<button type="button" id="magic">Magic</button>
<script>
function sayMagicWord() {
    alert('Shazam!');
}
let button = document.getElementById('magic');
button.addEventListener('click', sayMagicWord)
</script>
```

> NOTE: if you attach a listener by reference, pass the *name* of the function only! **Do not invoke the function**.

---

# Event Parameters

An event handler function can optionally accept a parameter -- usually called `event` (or just `e`) -- that contains [lots of information about the thing that just happened].

An [event object](https://developer.mozilla.org/en-US/docs/Web/API/Event) has many properties but the most important one is `event.target`, which points to the element where the action took place.

For instance, for a **click** event, `event.target` contains a pointer to the *element* that was clicked.

---

```html
<button type="button" id="presto">Presto...</button>
<button type="button" id="abra">Abra...</button>
<script>
var prestoButton = document.getElementById('presto');
var abraButton = document.getElementById('abra');

function sayMagicWord(event) {
  if (event.target === prestoButton) {
    alert('Change-o!');
  } else if (event.target === abraButton) {
    alert('Cadabra!');
  } else {
    alert('Shazam!');
  }
  console.log({event}); // for debugging
}

prestoButton.addEventListener('click', sayMagicWord)
abraButton.addEventListener('click', sayMagicWord)
</script>
```

---

# Event Bubbling & Capture

- Events are created by their elements
- After creation they move up the chain by default
- This behavior can be changed by using `cancel` on the listener

```html
<div onclick="alert('outer div')">OUTER DIV
  <div onclick="alert('inner div')">INNER DIV
    <p onclick="alert('paragraph')">Paragraph</p>
  </div>
</div>
```

---

# Bubbling Example

<iframe height="265" style="width: 100%;" scrolling="no" title="bubble-events" src="//codepen.io/Dangeranger/embed/GbjpbP/?height=265&theme-id=0&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/Dangeranger/pen/GbjpbP/'>bubble-events</a> by Joshua Burke
  (<a href='https://codepen.io/Dangeranger'>@Dangeranger</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

---

![event flow](https://res.cloudinary.com/btvca/image/upload/v1574445173/curriculum/eventflow_nyx1zw.svg)
