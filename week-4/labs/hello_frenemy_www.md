# Hello Frenemy WWW

## Welcome!

In this lab you will set up an input form where you can enter a name, and the page will greet that name with a fancy popup. We'll also make it so that if an enemy is entered it will alert us of that, and deny them entry

## Creating the Page

Begin by creating an html file and a seperate JS file

Link them together with a script tag `<script src='index.js'/>`

## Reading Properties

Looking at HTML elements in JS is fairly easy. Use a dom query. Access the properties as if the html element was an object (because it more or less is)

## Forms as Input

Inside the html <body>, lets set up the page by using a form element with one text and a corrisponding submit button

## The `<input>` Element

The <input> HTML element is used to create interactive controls for web-based forms in order to accept data from the user.

It also:
-specifies an input field where the user can enter data.
-is the most important form element.
-can be displayed in several ways, depending on the type attribute.

*Inputs can never have child nodes, only values*

## Writing to the DOM

We'll want the names displaying on the page, just put it in the display for now.

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

Lets build it out more: Make the alert modal flash different colors
