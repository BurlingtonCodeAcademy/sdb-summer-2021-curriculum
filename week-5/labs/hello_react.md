# React Holy Grail

## Objective

Get introduced to React by creating a one-page application.

## Learning

In this lab, you will recreate the classic [Holy Grail layout](https://en.wikipedia.org/wiki/Holy_grail_(web_design)) in React.

Topics:

- React components
- React JSX

## Achieving

Your work will result in:

- A page that resembles the Holy Grail layout.
- This page will be comprised of three components: the header, the content, and the footer. 

## Procedure

### Create your components

- [ ] Create three new components: Header.jsx, Content.jsx, and Footer.jsx
- [ ] In these three new components, set up their boilerplate code. Replace `ComponentName` with the appropriate name and insert text into the return statement so you know which component is being rendered.
```js
function ComponentName() {
  return (
    <div>
      This is the ComponentName component.
    </div>
  );
}
export default ComponentName;
```

### Import your new components into `App.jsx`

- [ ] Within the `App` component, import `Header`, `Content`, and `Footer`.
```js
import ComponentName from './ComponentName.jsx'
```
- [ ] Render your three imported components in the App component's return statement.
```js
 return (
    <main>
      <ComponentName />
    </main>
  );
```
**Remember, React renders components in top-down order.** 

### Style your components

- [ ] Refer to the Base wireframe at the following link: [React Holy Grail](https://www.figma.com/file/3LzHE1feUIla6ZfNUKyMhZ/react-holy-grail?node-id=0%3A1)
- [ ] JSX allows for HTML elements to be written in JavaScript. Apply CSS to them in the same way you have previously.

## Review

In this lab, you will have created your first React application with multiple components.

The software should:

- Have four total JSX files: App, Header, Content, and Footer.
- Have three of those components (Header, Content, and Footer) rendered on App.
- Match the given wireframe.
  
## Going Further

- Refer to the Going Further wireframe at the following link: [React Holy Grail](https://www.figma.com/file/3LzHE1feUIla6ZfNUKyMhZ/react-holy-grail?node-id=0%3A1)
- Create one or two more components to serve as ADs on the website. Incorporate timers to have the ad image change periodically.
