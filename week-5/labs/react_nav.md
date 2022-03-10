# React Router Nav

To practice utilizing documentation for a React library.

## Learning

In this lab, you will be using the React Router library and its components: `BrowserRouter`, `Routes`, `Route`, and `Link`.

- Library documentation
- React Router
- `BrowserRouter`, `Routes`, `Route`, and `Link` React Router components.

## Achieving

In this lab, you will create a navigation bar that, when the user clicks on the links, simulates React as a multi-page application. 

Your work will result in:

- A web page with a navigation bar.
- When the user clicks links in the navigation bar, it rerenders the page with a different component while simulating the appearance of a multi-page application.

# Procedure

- [ ] You will need at least four components: App, and three others of your choice.
- [ ] In `index.js`, reference the following documentation: [React Router v6 Overview](https://reactrouter.com/docs/en/v6/getting-started/overview). In the 'Configuring Routes' code snippet, replicate the nesting syntax of `<BrowserRouter>`, `<Routes>`, and `<Route>`.
- [ ] In your individual `<Route>`s, you will need to pass two props: `path` and `element`. Path will represent the URL fragment you want that component to be associated with. Element is where you pass in the component.
```js
<Route path = "/example" element = {<Example />} />
```
- [ ] In App, create your navigation bar. On the same documentation, reference the 'Navigation' section and utilize `<Link>`.
- [ ] In your individual `<Link>`s, you will need to pass the `to` prop. This prop should match the `path` of the component you want the user to navigate to.
- [ ] In your three other components, they should: contain unique content to distinguish them from each other, and a `<Link>` that returns the user back to App.

# Review

In this lab, you practiced utilizing a React library and understanding documentation. 

The software should:

- Consist of a landing page with a navigation bar.
- When the user clicks a link in the navigation bar, it simulates navigating to a different page. In reality, React Router is rendering components based on the URL. 
- Have four components: App and three others of your choice. They should all be visually distinguishable from each other.

## Going Further

- Style your landing page: [Frontend Mentor Huddle Landing Page](https://www.frontendmentor.io/challenges/huddle-landing-page-with-a-single-introductory-section-B_2Wvxgi0). This landing page mock-up is for an imaginary social media application called 'Huddle'. How could you continue the design language of this mock-up on your other components so they all have visual cohesion? You will need the style guide provided in the assets on Frontend Mentor.

**OR**

- In the previously linked documentation, scroll down 'Nested Routes'. See if you can implement them based on the documentation and your own research alone.
