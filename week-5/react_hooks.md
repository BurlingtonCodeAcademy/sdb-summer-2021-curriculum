# How to Use Hooks

Hooks can be used inside any functional React component, but they can *only* be used inside a functional React component, or a custom Hook. You can also use the same hook multiple times in the same component to set up different operations, or values.

You can **not** use Hooks in:

- the global name space
- class based components
- loops
- conditional statements
- nested functions
- anything that's not a functional React component

---

# How Hooks Work

Each Hook has a slightly different use case, but there are some aspects of Hooks which apply to all of them

Hooks are just functions that come with the React package that allow functional components to access state, and lifecycle methods. You can import them by targeting them directly in your import

> e.g. `import React, { useState } from 'react'`

Each Hook can be used multiple times, but it is worth noting that *order is important*.

Hooks must be rendered in the same order every time to work properly which is why you can't use hooks inside loops, or conditionals.

> Those curly braces around useState are important since `useState` is not the default export for the React package

---

# Benefits of Hooks

- the simplicity of a functional component with the power of a class based component
- allows related operations to be bundled together
- stateful logic can be reused between components
  - > Note: It's just the *logic* that is reused, not the values in state

---

# Types of Hooks

Your basic Hooks are:

- `useState`
- `useEffect`
- `useContext`

Less common Hooks are: 

- `useReducer`
- `useCallback`
- `useMemo`
- `useRef`
- `useImpreativeHandle`
- `useLayoutEffect`
- `useDebugValue`

`useState` and `useEffect` are by far the most common Hooks you will come across.

---

# Creating Custom Hooks

You can also create your own custom hooks by simply writing a function that performs the actions you want your hooks to take. This can be done to combine multiple hooks into one reusable operation, or to create an entirely new bit of functionality

---

# Hook Naming Conventions

It is important that you start the name of your custom Hook with `use` otherwise React won't recognize it as a valid hook.

> e.g. useMyCustomHook

---

# Refs, and Readings

- [Start here with the React docs](https://reactjs.org/docs/hooks-intro.html)