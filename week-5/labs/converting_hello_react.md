# React Dark and Light Mode

## Objective

To understand how to use the React.js front-end library to switch the style of a webpage from a light theme to a dark theme.

## Learning

In this lab, we will create a small React application that is able to use a component to switch the style of other components within the page. You will use inline styles, and then optionally understand how to add a `.someClassName` to react components to use CSS style sheets.

Topics:

- React State; `useState` and `setState`.
- React Style; `style` and `className`props.
- Passing `props` to child components.
- React and CSS

## Achieving

Your work will result in:

- A website whose styles can be changed by clicking a button.

## Procedure

### Create the child components

- [ ] The first thing you need to do is create three new files: `Header.jsx`, `Content.jsx`, and `Footer.jsx`. These will need to contain functional components that have the parameter of `props`. Reference `App.jsx` for what you need to set these up.
- [ ] `Header.jsx` should contain a `<h1>` title, and an image.
- [ ] `Content.jsx` should contain some `<p>` components with text.
- [ ] `Footer.jsx` should contain the author's name, and the date.

### Place the three child components within the parent App

- [ ] We will need to import our child components into `App.jsx`. We will also need to place them in `App`'s return statement.
- [ ] In the return statement, these three components will need to be wrapped in a div with a style prop of `styleMode`.

### Create inline style objects
- [ ] We wil need two objects, `darkMode` and `lightMode` that contain styles within. `darkMode` should set the background color to black and the font color to white. `lightMode` should set the background color to white and the font color to black.

### Create the `styleMode` state

- [ ] Create a new state variable named `styleMode` with an initial state of `lightMode`.

### Add the mode switching button

- [ ] Add a `<button>` element above the `<Header />` that toggles `styleMode`'s state.
- [ ] This button will need an `onClick` event that sets the current style. The callback function passed to `onClick` will need to use conditional logic to check `styleMode`and use `setStyleMode()` to change it to the opposite of what it currently is.

### Passing props to child components

- [ ] In `<Header />`,`<Content />`, `<Footer />`, we will need to pass `styleMode` as a prop to these components.
```js
<Example exampleProp = {exampleProp} />
```

### Using props in our child components

- [ ] In our three components, we will need a `<div>` that wraps all the other elements within the return statement. This `<div>` will have a style prop of `props.styleMode`.

### Test the button!

- [ ] When you click your button, the style of the page should toggle between your two style objects.

## Review

In this lab, we created a `styleMode` state and passed it as a prop to child components in order to toggle between dark and light mode on our page.

The software should:

- Be a website with three different components, `<Header />`, `<Content />`, `<Footer />` rendering on the page.
- Pass a `styleMode` state as a prop to the the child components.
- Have the style of the child components changed dynamically utilizing `props`.

## Going Further

- How could you leverage a CSS file with existing declarations? Could you apply a CSS `class` to the JSX components?

- What would be a downside to applying inline-styles to a React component? Remember that `style` is a prop, and props in React are immutable. What happens when you change them?

> Hint: to add a class to a component, use the prop name `className` instead of the reserved word `class`. Remember that JSX runs within JavaScript.
