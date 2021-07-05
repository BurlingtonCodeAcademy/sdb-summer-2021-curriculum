# Name Display

## Welcome!

The purpose of this lab is to practice managing state, and setting up controlled inputs. Remember; in React you don't want to directly manipulate the DOM. All page transformations should be done by manipulating your component's state

We are going to create a React component that has a form with two input fields for a first name, and last name. When the form is submitted we will display the full name on the page.

## Setting up React

Create a new directory named `react-apps`. Inside this directory tun the `npm init -y` command to prepare it for installing dependencies. Then install `create-react-app` using the command `npm install create-react-app`.

Now that we have a location in our file system where we can use `creat-react-app` let's use it to create our "Name Display" application.

Run the command `npx create-react-app name-display`. This should create a new directory called `name-display`, but it might take several minutes to completely install all the React dependencies. Wait for it to finish then `cd` into that directory, and run the command `npm start` to start your React server, and visit localhost:3000 to see the site.

## Make it Your Own

Now that we have a working React site let's go into the `src` folder, open up `App.js` and replace the starter code with our own component.

Delete everything in this file, and create a new class based component named `App`. Don't forget to import the `React` package in this file, and don't forget to export the component!

The `App` component will need:

- 3 properties in state, initially set to empty strings
  - `firstName`
  - `lastName`
  - `fullName`
- In the render method it will need:
  - A form with 3 input elements; Two text inputs, and one submit button
  - A display area that contains the `fullName` stateful property

## See the Name

To make sure the name is displaying properly on the page go ahead and hard code a value for your `fullName` property.

If everything is all set up this name should appear on the page. Change the value of the property in state, and the site should display the new name automatically.

Once you've changed the name a few times, and seen the page update accordingly set it back to an empty string.

# Controlled Inputs

React likes to be in complete control of the DOM using its virtual DOM, so when we start writing code to circumvent React, and directly manipulate the DOM React gets confused, and bugs start to creep into our code.

To effect changes on the page, even ones as minor as text appearing in a typeable field, we want to be referencing and manipulating our component's state rather than the DOM.

Input elements that draw their value from state are referred to as "controlled inputs". Let's make our two text inputs controlled inputs.

- Set a `value` property on each input equal to one of your stateful properties (`firstName`, and `lastName`)
- Set an `onChange` property on each element, and use it to create an event handler
  - On a change we want to update our stateful property with the *new value* of our *event's target*

If this is all set up well we should see the value updating in our text inputs as we type into them, otherwise we won't see any characters no matter how much you type.

## Displaying the Name Programmatically

Once we're tracking the values in our text fields we're ready to deal with the form submission.

Attach an `onSubmit` property to your `form` element, and create an event handler function that:

- Prevents the default event behavior
- Sets the `fullName` property to the value of your `firstName` and `lastName`
- Clears the form's inputs by *resetting your stateful properties*

## Celebrate

Congratulations! You're now manipulating the content on your page by using your Component's state. This is the heart of effecting page transformations, and tracking user interactions in React.
