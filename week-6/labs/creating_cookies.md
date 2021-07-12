# Creating Cookies

## Welcome!

The purpose of this lab is to get more practice sending data from the server to the browser in the form of a cookie.

In this lab we will be creating a site that uses the power of delicious baked goods (whoops! wrong kind of cookie) to set a color theme for the site, and have it persist across sessions.
[cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

## Creating the File Structure

- Create a directory called `cookie-theme` *or something to denote cookies in the file*

- cd in this directory and open VS Code with `code .`

- In this directory you will want to create a `public` folder
    -You will want to create an `index.html`, an `index.js` and a `style.css` inside the `public` folder.
    -Also create a `server.js` on the same level as the `public`

## Setting up the Server

- Set up a server with express. Here's a hint to get you started:

```js
const express = require('express');
const app = express();
const port = process.env.PORT || 5000;
```

## Create the Theme Picker

- Use DOM Scripting to toggle between some light and dark themes that will use cookies to store them.
- You will have to set up CSS Properties for both:
    ```
    body.dark-mode {
    background-color: a-dark-color;
    color: a-light-color;
    }
    body.light-mode {
    background-color: a-light-color;
    color: a-dark-color;
    }
    ```
- To Toggle between, set up some Buttons with DOM Scripting elements to target in your JS file.
    -`<button type="button" name="dark" onclick="toggleDarkTheme()" title="Toggle dark mode">Dark Theme</button>`
    -`<button type="button" name="light" onclick="toggleLightTheme()" title="Toggle light mode">Light Theme</button>`
    
## Get the Cookie

- Now create a function to set the cookies and check them using `document.cookie`
    -*Hint* Use `console.log()`s to log the cookies and check in the inspector
    
     
