# What is React

---

# Component Oriented Design

---

# The Component Class

---

# React Components

* Isolated pieces of a website or app
* Can be passed data from parent components in the form of `props`
* Can be rendered manually, or programatically
* Return JSX

---

# Using Components

* Typically the `index.js` initiates the components tree from the top level
* Can be made up of other components
* Child components are rendered by their parents
* Parents pass stateful data as props to children

---

# Using Arrays of Components

* Many components can be rendered at once
* Wrap the components in an array
* React will iterate over and render each
* Useful when rendering many of the same component, or sets of data

---

# Immutable Components

* Once components are rendered they cannot be updated manually
* Re-rendering the component is how to update them
* Re-renders are triggered when `state` or `props` change

---

# Granular Render Updates

![render performance](/images/granular-dom-updates.gif)

# Component Lifecycle

## Mounting

  * constructor()
  * static getDerivedStateFromProps()
  * render()
  * componentDidMount()

## Updating

  * static getDerivedStateFromProps()
  * shouldComponentUpdate()
  * render()
  * getSnapshotBeforeUpdate()
  * componentDidUpdate()

## Unmounting

  * componentWillUnmount()

## Errors

  * componentDidCatch()

# Lifecycle Methods Diagram

![react-component-lifecycle](/images/react-component-lifecycle.png)

<http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/>