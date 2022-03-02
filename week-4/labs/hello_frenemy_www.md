# Hello Frenemy WWW

## Objective

The purpose of this lab is to get more comfortable interacting with the DOM by creating a browser based version of our "Hello Frenemy" lab from the first week of the course.

## Learning

In this lab, we will be practicing with query selectors and the `<form>` HTML element. 

Topics:

- HTML.
- Query selectors.
- `<form>` element.

## Achieving

In this lab, you will bring your Hello Frenemy program into the browser. 

Your work will result in:

- A website that asks the user their name and has an input box for them to respond.
- Based on the name, the website either welcomes the user or tells them to go away.

## Procedure

### Setting up your HTML

- [ ] This website will need a few elements:
- [ ] An empty `<h2>` with an id of "computer-response".
- [ ] A form with an action of "/" and an id of "name-form".
- [ ] Within the form, a `<label>` for "user-input" with the text "What is your name?"
- [ ] Within the form, an `<input>` with the type of text and the id of "user-input".
- [ ] Within the form, an `<input>` with the type of submit.

### Getting our DOM elements

- [ ] In your JavaScript, you will need to use query selectors to get references to our three element nodes with ids.

### Adding the event listener to our form

- [ ] The variable used to reference "name-form" will need an event listener. This time, the event will be "submit" and the word `event` should be passed in as its argument.
- [ ] In order to access the data in our form, we will need to prevent the default behavior of the submit event. See this link for more information: [MDN Event.preventDefault()](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault)
- [ ] We will need to get the `.value` of our "user-input" element and assign it to a new variable.
- [ ] We will need to create an Array that contains the names of our enemies.

### Checking for enemies

- [ ] Inside of the event listener, we will need an `if...else` statement that determines if "user-input" is in our array of enemies.
- [ ] If "user-input" is an enemy, set the `textContent` of "computer-response" to "Go away!"
- [ ] Else, set the `textContent` of "computer-response" to greet the user by name.

## Review

In this lab, we translated our previous Hello Frenemy lab to work within the browser.

The software should:

- Have a labeled form where the user can input their name and submit it.
- If the submitted name is an enemy, the browser should tell the user to "Go away!".
- If the submitted name is not an enemy, the browser should greet them by name.

## Going Further

- After the submit event, the user input remains. How could you clear the field and "reset" it for better user experience?
- An enemy could sneak in with their name lowercase, in sticky caps, or by using their last name. How could you prevent that?
- How could you use CSS to emphasize the enemy and friend responses?
