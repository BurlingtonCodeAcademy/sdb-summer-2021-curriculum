# Hello Frenemy WWW

## Welcome!

The purpose of this lab is to get more comfortable interacting with the DOM by creating a browser based version of our "Hello Frenemy" lab from the first week of the course.

In this lab you will set up an input form where you can enter a name, and the page will greet that name with a fancy popup. We'll also make it so that if an enemy is entered it will alert us of that, and deny them entry.

## Creating the Page

Begin by creating an html file named `index.html`, and initializing it with the standard HTML shell generated with the emmet abbreviation <kbd>!</kbd> + <kbd>Tab</kbd>

Create a separate JS file named `main.js`, and link both files together by putting a script tag in your HTML with a `src` attribute pointing to your JavaScript file.

e.g. `<script src='main.js'/>`

## Forms as Input

Inside the html `<body>`, lets set up a location for user input by using a `<form>` element with one text input and a submit button

The `<form>` tags should contain your `<input />` elements

```html
<form>
  <input type="text" />
</form>
```

## The `<input>` Element

The `<input>` HTML element is used to create interactive controls for web-based forms in order to accept data from the user.

It also:

- specifies an input field where the user can enter data
- is the most important form element
- can be displayed in several ways, depending on the type attribute

For the purposes of entering a name we probably want an input with a `type="text"` attribute, and another `input` element with a `type="submit"` to act as our submit button.

To make it easier to target your elements in JavaScript you may also want to give them `id`s

*Inputs can never have child nodes, only values* so it's generally a good idea to make your inputs self closing tags.

## Reading Properties

Looking at HTML elements in JS is fairly easy. Use a *DOM query* to target an element and assign it to a variable. Once you have a reference to an HTML element you can use it like a JavaScript object, and access its properties using *dot notation*.

While property names in HTML are written in kabob-case when we bring them into JavaScript we write them in camelCase.

## Writing to the DOM

We'll want the names displaying on the page so let's make a new `div` on the page and give it an ID of "display"

Bring this element into your JavaScript file by using a DOM query, and assigning it to a variable.

We can then use this variable to manipulate the element's attributes and change the way it looks, and behaves on the page.

To write text content to an element you might find the `textContent` property most useful. Go ahead and reassign the `textContent` property of your "display" element to a new value, and see what happens.

## Submit Events

When the submit button is clicked a "submit" event will be fired by the `form` element. One of the things a submit event does, by default is redirect you to a new page or refreshes the current page. Attach an event listener to the form and prevent this behavior otherwise your JavaScript transformations will be lost when the page refreshes!

When the form is submitted we want to read the value of our text input, and write a greeting to that name in our display element. If an enemy's name is entered we should tell them to go away instead of greeting them.

## Clearing the Form

Upon the initial click, we want the inputs to clear so that another entry can be typed in.

*Hint: Reset the value of your input as an empty string*

## Enemy Alert!

Lets build it out more: Make the display area flash different colors when an enemy is detected!

We can create a random color generator by choosing three random numbers between 0 and 255, and using them to create an RGB string.

```js
let color = `rgb(${red}, ${green}, ${blue})
```

We can then set up a timing function that will change the background of our display area to a different color every specified number of second.

To access your CSS properties in JavaScript you will need to access the `style` property of an element, and you can then freely manipulate your style properties. It is worth noting that style properties are camel case in JavaScript even though they are kabob case in CSS

## Going Further

- Try changing your display area from a section of the page to a [modal dialog box](https://medium.com/@nerdplusdog/a-how-to-guide-for-modal-boxes-with-javascript-html-and-css-6a49d063987e)
