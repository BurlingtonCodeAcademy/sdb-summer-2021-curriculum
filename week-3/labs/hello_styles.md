# Hello Styles

## Objective

The purpose of this lab is to understand how CSS styles apply to structured HTML elements within a web page.

## Learning

In this lab, we will expand upon our previous lab [Hello HTML](https://online.uprighted.com/lessons/written/hello-html) by styling it with an external CSS sheet. We will also be practicing referencing a wireframe for creating our design. This lab is based off a real world scenario you might encounter in your role as a software developer; you may not be the one designing the websites, but you will be the one bringing them to life.

If you did not previously complete Hello Html, you can find a basic completion [here](https://replit.com/@limzkil/hello-html#index.html) to work with.

Topics:

- Utilizing a given wire frame.
- Styling with CSS.

## Achieving

In this lab, we will utilize a given wire frame to style our website with CSS according to its guidelines.

**Note**: While you Google around, you may come across the flexbox and grid CSS layout models. Do **not** use these for this lab! `Margin` and `padding` and other `display` properties will be a good place to start for this challenge.

Your work will result in:

- A website that closely matches the given wire frame.

## Procedure

### Duplicating and renaming the `hello-html` directory

- [ ] Duplicate your `hello-html` directory. We want the new version to be in the same folder the original is, not inside of it.
- [ ] Rename your duplicated directory to `hello-styles`.
- [ ] Open `hello-styles` in VScode.
- [ ] If you completed the Going Further, remove any inline styling attached to the semantic divs. 

### Creating the `styles` subdirectory and `styles.css`
- [ ] Inside of `hello-styles`, create a new directory named `styles`.
- [ ] Inside of `styles`, create a new filed named `styles.css`
- [ ] `styles.css` is where all of your CSS will be written.

### Linking `styles.css` to `index.html`
- [ ] Inside of `index.html`, you will need to link your stylesheet.
- [ ] You will find information on how to do this at the following link: [Freecodecamp's How to Link CSS to HTML](https://www.freecodecamp.org/news/external-css-stylesheets-how-to-link-css-to-html-and-import-into-head/).
- [ ] In the `src` attribute for the link, you will need to route your link through the `styles` subfolder to reach `styles.css`.

### Opening the wireframe

- [ ] Click the following link to open the wire frame: [Figma Wire Frame](https://www.figma.com/file/XfSzyWby8nkpIolSql6R4S/hello-styles-wireframe?node-id=0%3A1).
- [ ] **Note:** This wireframe is not "pixel perfect" so don't stress having it match dimensions exactly. We are looking to capture the spirit of the wireframe.

### Understanding the wireframe

- [ ] This wireframe has areas that correspond to the semantic divs you already have from Hello Html.
- [ ] `<header>` matches the HEADER TEXT areas.
- [ ] `<nav>` matches the LINK areas that contain four links.
- [ ] The white boxes with black diagonal lines should be placeholder images utilizing the `<img>` tag.
- [ ] `<main>` matches the MAIN TEXT areas. You will note that on the ABOUT PAGE, there are two MAIN TEXT areas with space between them. This is intentional.

### Styling the divs

- [ ] You will need to utilize [CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) in order to style your divs. `id` and `class` are the most common utilized. 
- [ ] You will also need to utilize [CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference). As mentioned earlier, `margin`, `padding`, and `display` will be the most useful for achieving the layout.

## Review

In this lab, we have translated a wireframe to a website utilizing CSS.

The software should:

- Be a styled website whose design matches that presented in the wireframe.

## Going Further

- Customize the colors on the website.
- Import fonts and utilize them.
- Style your additional pages created in [Hello HTML](https://online.uprighted.com/lessons/written/hello-html). Go back to that lab description for a refresher on how to create them if you did not. Try to have the visual design of these additional pages be coherent with the styling of the first two.

