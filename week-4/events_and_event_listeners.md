# Event Listeners

In the first we discussed, listening for events and handling events that have occurred.

- All HTML elements can listen for certain events that are relevant to the element
  - Buttons listen for `onclick`
  - Forms listen for `onsubmit`
- DOM Nodes also have an `addEventListener` method to extend this feature to handle custom circumstances.

---

## Event Listeners Cont.

[Introduction to Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
[addEventListener Documentation](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

> Explore the above links. Be prepared to share what you found with the group.

---

## Handling Events

An **event handler** is what you want the computer to do when an event happens.

Before, we discussed kinds of events, like `onclick`.
Now, we are discussing _what to do_ when `onclick` occurs.

```js
// Grab the relevant element from the DOM
let button = document.getElementById("magic");
// Use addEventListener to tell button how to handle being clicked
button.addEventListener("click", () => {
  alert("Abracadabra!");
});
```

> NOTE: Using arrow functions for event handlers is a **good idea**, since they will restore `this` to the same object as when the listener was added.

---

## Exercise: Make a Button Count

Let's write an event listener together:

> <https://replit.com/team/education-team/dom-scripting-exercise>

---

## Referencing Event Handlers in Event Listeners

If you have already defined an event handler function, you can attach it by reference:

```html
<button type="button" id="magic">Magic</button>
<script>
  function sayMagicWord() {
    alert("Shazam!");
  }
  let button = document.getElementById("magic");
  button.addEventListener("click", sayMagicWord);
</script>
```

> NOTE: Why do we not invoke the function here? What does it mean to pass by reference?

---

## Event Handler Parameters

- The browser will always pass an [Event instance](https://developer.mozilla.org/en-US/docs/Web/API/Event) to your handler function as its first argument.
- To account for this, you'll often see `e` as the parameter
- Within `e` (the Event instance), there is a property called `target` -- `e.target`.
  - `target` represents the node the person interacted with -- where the `Event` occurred within the DOM.
  - Example: If you `click` a `button`, the `button` is the target of the `click` `event`.

---

```html
<button type="button" id="presto">Presto...</button>
<button type="button" id="abra">Abra...</button>
<script>
  var prestoButton = document.getElementById("presto");
  var abraButton = document.getElementById("abra");

  function sayMagicWord(event) {
    if (event.target === prestoButton) {
      alert("Change-o!");
    } else if (event.target === abraButton) {
      alert("Cadabra!");
    } else {
      alert("Shazam!");
    }
    console.log({ event }); // for debugging
  }

  prestoButton.addEventListener("click", sayMagicWord);
  abraButton.addEventListener("click", sayMagicWord);
</script>
```

---

## Event Bubbling & Capture

- Elements make their respective Event instances.
- After the Event instance is made, it moves up the DOM tree by default.
- This behavior can be changed by using `cancel` on the listener

```html
<div onclick="alert('outer div')">
  OUTER DIV
  <div onclick="alert('inner div')">
    INNER DIV
    <p onclick="alert('paragraph')">Paragraph</p>
  </div>
</div>
```

---

## Bubbling Example

Let's see bubbling in action:

<https://replit.com/team/education-team/event-bubbling>

---

<img src ="https://res.cloudinary.com/btvca/image/upload/v1574445173/curriculum/eventflow_nyx1zw.svg" width="700px" alt="event flow diagram referenced in the docs">

---
