# Lab: Hello File Server

## Objective

To understand how to use the Express.js library to create a back-end file server.

## Learning

In this lab we will be creating a server that serves any static files, such as HTML, CSS, or JavaScript.

## Achieving

In this lab, you will create a simple file server using Express.js, use that server to access files on a web host, and then limit the files which are served to only those within a specific folder.

## Procedure

### Create a Server with Express

- [ ] Create a project directory by running the NPM command below within the `code` directory.

```sh
npm init -y static-server
npm add express
```

- [ ] Add the starter code below to create a static file server.

```js
const express = require('express');
const app = express();
const port = process.env.PORT || 5000

app.use(express.static('.'));
app.listen(port, () => console.log(`Server listening on http://localhost:${port}!`));
```

- [ ] Add an HTML file within the project directory named `index.html`.
- [ ] Add some simple content to the HTML file, such as the code below.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Example Pave</title>
  </head>
  <body>
    <h1>Hello, Express!</h1>
  </body>
</html>
```

- [ ] Start the server by running `index.js` using `node`.
- [ ] Visit your running server at `http://localhost:5000` with a web browser.

### Visiting the private file `package.json`

- [ ] Start the server, if it is not already running.
- [ ] Visit the following file `http://localhost:5000/package.json`
- [ ] Ask yourself if you would want a visitor to view the project's `package.json`

### Limit the Express server to a `public` directory

- [ ] Create a directory named `public` within your project directory.
- [ ] Move the `index.html` into the `public` directory.
- [ ] Update the `index.js` file to limit visitor access to the `public` directory.

```js
// update the line in the sample code to match
app.use(express.static('public'))
```

### Add more files to serve

- [ ] Create at least two more HTML files within the `public` directory.
- [ ] Link the two new files to the `index.html` using Anchor tags, e.g. `<a href="someFile.html" >`
- [ ] Visit the other pages by clicking the links from the `index.html` page.
- [ ] Visit the other pages navigating to them directly by visiting `http://localhost:5000/someOtherPage.html`

## Review

In this lab, you practiced creating an Express back-end server that can send arbitrary files from the server to a browser client. You created a default page for the server to send, as `index.html`, and also created additional files that can be visited from the `index.html` or directly.

## Going Further

- Inspect the `headers` of the response from the server to the client in the browser development tools.
- What happens if you visit a page that does not exist within the `public` directory?
- Can you find a way to send a default page to the client, such as a `404.html` instead of an error?
- What HTTP code should you use as a `header` when sending the `404.html` page?
- Add a `start` script to the `package.json` file to make it easier to start your server.
  - Now, start your server with `npm start` instead of `node index.js`.

```js
// add the following within package.json
{
  "scripts": {
    "start": "node app.js"
  }
}
```
