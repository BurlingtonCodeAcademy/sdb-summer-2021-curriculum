# React Name Display

## Objective

To understand how to use the React.js front-end library to create components which automatically update based on changes to the application state.

## Learning

In this lab, we will create a small React application that tracks the values of a person's name, and then greets that person by their name along with a friendly message.

Topics:

- React State; `useState` and `setState`
- React Forms; `onChange`

## Achieving

Your work will result in:

- A component that displays a person's name, along with a friendly message.
- A form that allows for input from a human, to enter their full-name.

## Procedure

### Create a single component to display a message

- [ ] Use the `App` component to render (display) a friendly message.
- [ ] Create a variable within the `App` component to reference your message.
- [ ] Update the `App` component message to use the variable containing the message.

### Add a form for a human to enter their full-name

- [ ] Within the `App` component, add a `<form />` child component.
- [ ] Within the `<form />` component, add three `<input />` child components that will take in the person's first name, middle name, and last name.
- [ ] Use the `useState` hook to create a variable corresponding to each of the three `<input />` components, and a function that updates that variable when called.

### Connect the form to the component to update on change

- [ ] Attach an `onChange` event handler to each `<input />` component.
- [ ] For the value of the `onChange` handler, define an inline Arrow Function that uses the `setSomeVariableName` function corresponding to the `<input />` element that is updated by the human.

E.g.

```jsx
  // arrow functions can be defined inline
  <input onChange={(e) => { setSomeVariableName(e.target.value)}}
```

### Use the `state` variables to compute a message to the human

- [ ] Use the `someStateVariable`'s that you created above in the component that messages the human by their full name.
- [ ] Combine the `message` variable and the state variables for the full message.

## Review

In this lab, we will have created a small React application that tracks the values of a person's name, and then greets that person by their name along with a friendly message.

The software should:

- Take in the user's full name in a form
- Print their full name in a friendly message to the page.

## Going Further

- How you could you extract the inline `onChange` handler functions within the `<input />` components to use a shared `onChange` handler, rather then each using their own?

- Notice how the message updates when the user types new values into the `<input />` components. How could you make the form only update the message when the user **submits** the form?
