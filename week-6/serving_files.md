# Serving Files

* **Serving** a file refers to sending a file from the backend to the user.
* **Static**
    * Files saved on the server computer that do not change in real time.
* **Dynamic**
  * Files created on the fly for every request.

---

# Serving Static Files

In earlier lessons, you may have used the `live-server` VSCode extension to serve your projects before we began learning React.

Live-server is an example of a static file server built into Node.

This tool is useful for local development but not great for production deployments. We don't have very much control over it.

---

# Creating a Static File Server using Express

* Express comes with its own static file server

```js
let staticServer = express.static('.')
app.use( staticServer )
```

---

# Headers: Content-Type  

* files usually tell you what file type they are
    * e.g. .html, .js, .css
* URLs often do not do this
    * `https://developer.mozilla.org/en-US/docs/Web/JavaScript` is a route that serves an HTML page. Notice how it doesn't have `.html` at the end.
* Web servers must read the file type extension and use the `Content-Type` header on the request to tell the client what format the file is in
    * `text/html` means HTML
    * `application/javascript` means JavaScript
    * `text/css` means CSS Stylesheet
    * ...these are called *MIME Types* (after the Multipurpose Internet Mail Extensions specification)

---

# Headers: Dev Tools

![headers](https://res.cloudinary.com/btvca/image/upload/v1626093503/content-type_zimyop.png)

