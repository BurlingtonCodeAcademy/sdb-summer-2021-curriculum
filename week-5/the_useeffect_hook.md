# useEffect

Like all other hooks `useEffect` must be directly imported from React before you can use it.

`useEffect` is used to setup what React refers to as "side effects." These are operations which fall outside the normal React render cycle, such as direct manipulation of the window objects, fetching data, setting up event listeners, or performing cleanup tasks.

---

# use Effect in the Lifecycle

You can think of `useEffect` as an all-in-one function for the `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` lifecycle methods

`useEffect` can clean up after itself by returning a clean up function, but not every operation needs to be cleaned up.

---

# useEffect with no Cleanup

Effects that don't require a cleanup are actions that should be taken on every render. e.g. updating the `title` of your `document`. You can set these up by passing a callback function which performs the necessary action. This callback will be called every time the component renders, or rerenders

> If you wanted to update the title of the document from the previous lab to reflect the user's full name you could add a `useEffect(() => { document.title = fullName + "'s page"})` to your component

---

# Cleaning up After useEffect

If you are drawing data from an outside source, or you're subscribing to an external service you probably need to clean up after your effect to prevent a memory leak. To do this `return` a function from your `useEffect` callback that performs the cleanup tasks

---

# Clean useEffect Example

```js
useEffect(() => {
    if(user) {
     chatService.openConnection(user.id);
    }

    return function() {chatService.close()}
  })
```

The function that is returned from our callback (`function() {chatService.close()}`) will be called during the `componentWillUnmount` lifecycle stage


---

# Fetching Data

* Most React frontend apps (and most web apps in general) need server data
* The browsers `fetch` API can be used to fetch data from databases or other locations on the internet
* Fetched data should be stored in state, and the values in state are rendered to the page
* It is generally best practice to fetch when the component first mounts, during the `componentDidMount` lifecycle process

---

# Fetching Data Cont.

* Render an empty component first
* Get data after it has been rendered
* Re-render by setting the fetched data in state
* We can access the state and lifecycle render methods by using the `useState` and `useEffect` hooks respectively

---

# Fetching Data With Hooks

To fetch data (and store it) in a functional component we need to use Hooks

- first set up a property in state, and an updater function using `setState`
- then fetch the data with `useEffect`
- and use your updater function to set the fetched data in state
- use your state property to conditionally render data to the page when it's loaded

> Note: Changing state triggers a re-render, a re-render triggers `useEffect` so remember to wrap your state changes in conditionals, or you'll be trapped in an infinte render cycle.

---

# Fetching Data Example

```jsx

function DisplayPost(props) {
  const [post, setPost] = useState(null)

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts/1')
      .then(res => res.json())
      .then(res => {
        setPost(res)
      })
  })
  
  return(
    <ul>
      {post}
    </ul>
  )
}

```

---

# Fetching Data - Handle Errors

* Errors in `fetch` using APIs happen
* Do not let an error ruin your page by raising in production
* Better to wait/retry and present a nice message

---

**Component with Error Handling**

```jsx
function AuthorList(props) {
  const [authors, setAuthors] = useState(null)

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(res => res.json())
      .then(res => {
        setAuthors(res)
      }).catch((err) => {
        alert('Something went wrong...')
        console.error(err.message)
      })
  })
  
  return(
    <ul>
      {authors ? authors.map((author) => {
        return <li>{author.name}</li>
      }) : 'loading...'}
    </ul>
  )
}
```

---

# Fetching Data - Example

<https://codesandbox.io/embed/p99mqrq9z0>

<p data-height="500" data-theme-id="light" data-slug-hash="gjELaj" data-default-tab="js,result" data-user="Dangeranger" data-pen-title="Fetching API Data" class="codepen">See the Pen <a href="https://codepen.io/Dangeranger/pen/gjELaj/">Fetching API Data</a> by Joshua Burke (<a href="https://codepen.io/Dangeranger">@Dangeranger</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

---

# useState in useEffect

Using `useState` inside a `useEffect` callback is a fairly common practice, but you want to be a little careful when doing this

- `useState`'s updater function triggers the `componentDidUpdate` lifecycle event
- The callback function for `useEffect` gets called every time the component updates
- Using the updater directly inside your `useEffect` callback causes an infinite loop
- This is comparable to using `this.setState` inside `componentDidUpdate` in a class based component
