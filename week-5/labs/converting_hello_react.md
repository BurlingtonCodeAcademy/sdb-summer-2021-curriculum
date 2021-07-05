# Class to Functional Conversion

## Welcome!

The purpose of this lab is to get you more familiar with functional React Components, and the parallels between them and class based Components by having you convert a class based component to a functional Component.

## Hello Again Name Display

Let's build off of an application we've already created. Go ahead and get back into the `name-display` lab we created previously. Run through it, and re-familiarize yourself with the way it behaves, and the code that makes it all work.

We'll be creating a new component to put onto the page that will have the same elements and behavior, but will be written as a functional component instead of a class based component

## The Component Tree

Create a new JS file in your `src` folder for your new component. I will refer to this component as `FunkyName` from now on, and will refer to the file as `FunkyName.js`.

The component tree is a general term to describe the relationship between components, and which components render which other components. Currently our site has an `index` component found in `index.js` which renders our `App` component so our component tree is fairly simple:

```
index
|
React.StrictMode
|
App
```

Look into `index.js` to see how it's rendering `App`.

We can display our `FunkyName` component instead of our `App` component by replacing `<App />` in our `index` component with `FunkyName`. To do this we will first need to import `FunkyName` into `index.js` by using the es6 browser import syntax `import FunkyName from "./FunkyName.js"`. Then we can replace the `App` component in `index`'s return statement with the `FunkyName` component.

## Extracting the Render Method

An oversimplification of React Functional components is that they are essentially the `render` method of a class based component.

A functional component is a named function that takes `props` as it's only argument and returns some JSX. Then we can use this component in the exact same way we would a class based component; by importing it where we need it, and putting it into JSX syntax. Under the hood *functional components are compiled the same as class based components* so they behave the same way on the browser.

If we want our `FunkyName` component to render the same elements that `App` currently renders we can extract the return statement of our `render` method in `App` and use that as the return value for `FunkyName`

**But don't copy and paste!** Some aspects will change when moving from a class based to a functional component. We lose access to all our lifecycle methods, and our `setState` method so we need to remove any references to the state object or `this`. Instead we will use some variables, and a special type of function called a "hook" to access state.

## Hooks in Brief

In functional components you don't have access to any of the lifecycle methods, or any other React class based methods, but we still don't want to directly manipulate the DOM so we need some way to access `state`. This is where hooks come in.

Hooks allow us to *hook into* the React lifecycle events from a functional component. We will be using the `useState` hook to track, and manage our new component's state.

The first step to using `useState` is to import it from react

  - `import {useState} from 'react'`

Next we will set up two variables, for each stateful property using array destructuring, and `useState`

  - `const [property, setProperty] = useState(initialValue)`

This creates a property in state, with an initial value, and an updater function. We can then use our `setProperty` function to update our state.

We could set up a controlled input using the values from the call to `useState` like so:

```jsx
<input
  type="text"
  value={property}
  onChange={(evt) => {setProperty(evt.target.value)}}
/>
```

`setProperty` takes the new value we want to set as `property` in our state.

> Note: That there is no `this` keyword as we are not in a class, and so `this` will not point to what you want it to.

## Putting it Back Together

To rebuild the functionality of our name display we'll need to bring our stateful properties back in by using the `useState` hook to set up our three properties `firstName`, `lastName`, and `fullName` along with the updater functions for those properties.

Each call to `useState` can be used to set a single stateful property, and updater function so we will need to call `useState` 3 times to set up these variables.

In your render, instead of going through your `state` object to access the value of the property you can just use the variable directly. To update it you use the updater function which replaces `this.setState`

## Test it Out

Once you've changed the way the program is tracking and maintaining state, and replaced the `App` component with `FunkyName` in your `index.js` run the file, and watch in amazement as it does the exact same thing as before. But with a functional component!
