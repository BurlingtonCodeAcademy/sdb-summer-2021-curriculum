# React Libraries

There are many different plugins for React. These are packages that extend React's functionality event further or allow React to more easily deal with different technologies. 

This lesson focuses on learning how to use [React Router](https://reactrouter.com/docs/en/v6) for creating the illusion of pages within your application.

---

## Why use Libraries?

Libraries allow us to

- Solve problems more thoroughly, especially if they are very complex.
  - e.g. Time zones
- Share our knowledge and work with others.
- Use the knowledge others have shared.
- Extend the basic functionality of the language.
- Make "wrappers" around other technologies to make them easier to use.
  - e.g. React Leaflet

---

## Routing with React Router

- Routing refers to navigating to different pages in an app that have their own URLs.
- If our entire React application is in one div in one file, it's not clear how we create the experience of pages.
- React Router allows us to mimic this behavior and include features like page history so that the back button works.

---

## React Router Components

React Router comes with components to help us create pages and send users to those pages:

- `<Link />` A component you use instead of the `anchor` tag.
- `<Routes />` A component that holds all your pages.
- `<Route />` A component that shows your page when on a certain URL.
- `<BrowserRouter />` A component that mimics the browser's routing behaviors -- including the ability to use a history to go back and forth.
- `<Navigate />` A component that is used to redirect the user to a different page (good for when someone is not logged in or to send someone to a 404 page).

---

## React Router Hooks and Methods

In addition to some components, React Router gives us some hooks:

- `useParams` Grab variable data out of a URL path.
- `useRoutes` An alternative to `<Routes />`.
- `useSearchParams` Read and modify the query string in the URL for the current location.
- `navigate` Send the user to a specific route.

---

## Simple Router Example

```jsx
import { render } from "react-dom";
import { BrowserRouter, Routes, Route, } from "react-router-dom";
render(
  <BrowserRouter>
    <Routes>
      <Route path="/" element={<App />}>
        <Route index element={<Home />} />
        <Route path="about" element={<About />} />
        <Route path="contact" element={<Contact />} />
      </Route>
    </Routes>
  </BrowserRouter>,
  document.getElementById("root")
);

```

---

## Nested Router Example

```jsx
import { render } from "react-dom";
import { BrowserRouter, Routes, Route, } from "react-router-dom";
render(
  <BrowserRouter>
    <Routes>
      <Route path="/" element={<App />}>
        <Route index element={<Home />} />
        <Route path="teams" element={<Teams />}>
          <Route path=":teamId" element={<Team />} />
          <Route path="new" element={<NewTeamForm />} />
          <Route index element={<LeagueStandings />} />
        </Route>
      </Route>
    </Routes>
  </BrowserRouter>,
  document.getElementById("root")
);
```

---

## Practice: Making Pokemon Pages

<https://replit.com/team/education-team/react-router>
