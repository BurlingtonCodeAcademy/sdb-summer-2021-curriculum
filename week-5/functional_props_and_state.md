


# useState

The first step to using `useState` is to import it from react

  - `import {useState} from 'react'`

Next we will set up two variables using array destructuring, and `useState`

  - `const [property, setProperty] = useState(initialValue)`

This creates a property in state, with an initial value, and an updater function. We can then use our `setProperty` function to update our state.

  - (evt) => {setProperty(evt.target.value)}

`setProperty` takes the new value we want to set as `property` in our state. Note that our updater function is often wrapped in an event handler.

---

# useEffect

Like `useState` `useEffect` must be directly imported from React before you can use it.

`useEffect` is used to setup what React refers to as "side effects." These are operations which fall outside the normal React render cycle, such as direct manipulation of the window objects, fetching data, setting up event listeners, or performing cleanup tasks.

You can think of `useEffect` as an all-in-one function for the `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` lifecycle methods

`useEffect` can clean up after itself by returning a clean up function, but not every operation needs to be cleaned up.

---

# useEffect with no Cleanup

Effects that don't require a cleanup are actions that should be taken on every render. e.g. updating the `title` of your `document`. You can set these up by passing a callback function which performs the necessary action. This callback will be called every time the component renders, or rerenders

> If you wanted to update the title of the document from the previous lab to reflect the user's full name you could add a `useEffect(() => { document.title = fullName + "'s page"})` to your component

---

# cleaning up after useEffect

If you are drawing data from an outside source, or you're subscribing to an external service you probably need to clean up after your effect to prevent a memory leak. To do this `return` a function from your `useEffect` callback that performs the cleanup tasks

If we were subscribing to a chat service we might set it up something like this: 

```js
useEffect(() => {
    if(user) {
     chatService.openConnection(user.id);
    }

    return function() {chatService.close()}
  })
```

The function that is returned from our callback (`function() {chatService.close()}`) will be called during the `componentWillUnmount` lifecycle stage.

---

# Fetching with Functional Components

A very common use of `useEffect` is to fetch data, but you have to be a little careful when doing so...

Because `useEffect` combines `componentDidMount` and `componentDidUpdate` it fires its callback when the page first loads, and then again everytime the component re-renders. Changing state causes a re-render so if you forget to wrap your `setStateProperty` function in a gaurd clause you can get trapped in an infinite render cycle.

---

# Example Code

`useEffect` and `useState`combined should look something like this:

```js
function ShowData(props) {

  const [data, setData] = useState(null)

  useEffect(() => {
    if(!data) {
      fetch(someURL)
        .then(res => res.json())
        .then(jsonData => {
          setData(jsonData)
        })
    }
  })

  return (
    <div>
      { data }
    </div>
  )
}
```

---

