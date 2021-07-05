# React Nav Bar

## Welcome!

The React Router framework is a powerful tool in your arsenal as a developer. It allows you to build React applications (which are always single page web apps) that *behave like multi-page web apps!*

Let's practice using React Router by setting up a simple site with a navigation bar that will allow us to jump between different pages as if we were navigating  on a multi-page web app while keeping a consistent header, and nav bar.

## Setting up React

Use `create-react-app` to set up a new React application called `react-nav`. Don't forget to remove the starter code in the `App` component!

To bring in React Router run the command `npm install react-router react-router-dom` from inside your `react-nav` directory.

Create 5 new components, which should all live in separate files:

- Header
- Nav
- Home
- About
- Contact

In the `Home`, `About`, and `Contact` components add some unique content so you can tell them apart.

Import all of them into your `App` component. We will also need a few *prebuilt* components from React Router. Namely the `Switch`, `Route`, and `BrowserRouter` components which you can bring in by importing them from `react-nav`

```jsx
import {Switch, Route, BrowserRouter} from "react-router"
```

## Getting Ready for Routing

In your `App` component use the `BrowserRouter` component to contain all other content on the page. `BrowserRouter` gives the other React Router elements access to the `history` object which is what allows React Router to respect the URL path, and cause your React application to behave like a multi-page web app.

Render your `Head` and `Nav` components at the top of the page and then open up a `Switch` component.

## Using `Switch`

The `Switch` component should have both an opening and closing tag. **It should *not* be self closing** since we will need to put other components inside the `Switch` component.

The switch component will limit our routes so that only one route can be displayed at a time.

Currently our `App` component's return statement should look something like this:

```jsx
<BrowserRouter>
  <Header />
  <Nav />
  <Switch>
  </Switch>
</BrowserRouter>
```

## Creating Routes

The `Route` component is what allows us to tell our application which component should be displayed for a given path. Let's set up 3 `Route` components inside our `Switch` component (between the opening and closing tags).


Each Route component will need 2 properties, `path` and `component`. The `path` should equal a string that is the path you will visit and the `component` is the component you want to be displayed when you visit that path through the URL. We could set up our `Home` component to be displayed when we're at `"/"` like so:

```jsx
<Route exact path="/" component={Home} />
```

Note that we also add the `exact` property to this route since it is going to `"/"` and the `Route` will actually match any URL that starts with the desired path unless we give it the `exact` property. The other `Route` components shouldn't need the `exact` property. Go ahead and set up the routes for the other 2 components. Try visiting those paths by starting the app, and putting the routes into the url e.g. `https://localhost:3000/about` to get to the about page.

## Creating the Nav Bar

Having to enter the routes into the address bar isn't exactly the best user experience so lets set up a navigation bar to allow our user to move around our site more easily.

In our `Nav.js` file we will need to import a `Link` component from React Router. Once we've imported our `Link` we can use it to set up... links! They operate in a similar manner to an `a` tag, but are designed to work with React Router, and instead of an `href` property they get a `to` property. We could set up a link to take us back to the home page like so:

```jsx
<Link to="/">Home</Link>
```

Set up links going to each of your three pages; Home, About, and Contact.

Style the site, and make it look pretty! Admire your fully armed, and operational multi-page(ish) React application

## The Catch All route

We can also set a `path` on a route to `"*"`. This creates a "catch all" route that will accept *any path*. Since route matching is always top down, and we're using a `Switch` component to only show one component at a time, we can set up a catch all route at the bottom of our switch statement to handle any unexpected paths.

This is commonly used to set up a custom 404 page.

## Taking it Further

What if we wanted to pass props to one of our routed components? The way we've set this up that's currently impossible.

**But** we don't need to set our `component` on the `Route` as a pre-built component. We can instead define a new component *inline* by instead using the `render` property! This will allow us to define an anonymous functional component on our route that returns an initialized component which we *can* pass props to. Go ahead and try this out on one of your routes!
