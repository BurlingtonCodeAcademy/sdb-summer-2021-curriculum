# useState

The `useState` hook allows you access to a functional component's state.

The first step to using `useState` is to import it from react

  - `import {useState} from 'react'`

Next we will set up two variables using array destructuring, and `useState`

  - `const [property, setProperty] = useState(initialValue)`

---

# Using `useState`

Calling the `useState` hook creates a property in your component's state object, with an initial value, and an updater function. We can then use our `setProperty` function to update our state.

  - (evt) => {setProperty(evt.target.value)}

`setProperty` takes the new value we want to set as `property` in our state. Note that our updater function is often wrapped in an event handler.
