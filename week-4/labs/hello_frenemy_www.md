# Hello Frenemy WWW

## Welcome!

In this lab you will set up an input form where you can enter a name, and the page will greet that name with a fancy popup. We'll also make it so that if an enemy is entered it will alert us of that, and deny them entry.

## Creating the Page

Begin by creating an html file named `index.html`, and 

Create a separate JS file, and link both files together with a script tag in your HTML with a `src` attribute pointing to your JavaScript file. e.g. `<script src='main.js'/>`

## Reading Properties

Looking at HTML elements in JS is fairly easy. Use a dom query. Access the properties as if the html element was an object (because it more or less is)

## Forms as Input

Inside the html <body>, lets set up the page by using a form element with one text and a corresponding submit button

## The `<input>` Element

The `<input>` HTML element is used to create interactive controls for web-based forms in order to accept data from the user.

It also:

- specifies an input field where the user can enter data
- is the most important form element
- can be displayed in several ways, depending on the type attribute

For the purposes of entering a name we probably want an input with a `type="text"` attribute.

*Inputs can never have child nodes, only values*

## Writing to the DOM

We'll want the names displaying on the page so let's target or "display" element using a DOM query.

Store that value in a variable, and we can then manipulate the element's attributes to change the way it looks, and behaves on the page.

To write text content to an element you might find the `textContent` property most useful.

## Clearing the Form

Upon the initial click, we want the inputs to clear so that another entry can be typed in.

*Hint: Set the value as an empty string*

## Submit Events

When the submit button is clicked, an alert should display a personalized greeting OR tell our enemies "You shall not pass"

There are two properties that effect the submit event, the `method` and the `action`. (These will be covered in depth during our lessons on servers)

## Modal Dialog Boxes

Display areas are boring. Let's turn it into a modal!

Styling modals, tracking *state*.

## Enemy Alert!

Lets build it out more: Make the alert modal flash different colors when an enemy is detected! 
