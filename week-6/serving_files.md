# Serving Files

At its core, HTTP is a *file transfer protocol*.

* the *path* element of a URL is based on a Unix file path
* most web servers directly map incoming URL paths to filesystem paths
* because these files are stored on disk on the server, they are called *static files*
  * to distinguish from *dynamic pages* (aka *routes*) which the server will create on the fly for every request 

---

# node-static

In earlier lessons, you may have used the `node-static` package, or the `live-server` VSCode plugin to serve your HTML, JS, CSS, images, etc...

*node-static*, and *live-server* are standalone static file servers built in NodeJS

They're useful for local development but not great for production deployments

---

# static file server in Express

* Express comes with its own static file server
* Using it is a one-liner: 

```js
app.use(express.static('.'))
```

---

# index.html

A little historical note...

* in the early WWW, visiting a directory always showed a list of all the files in that directory
* this list was called an *index* since it was in alphabetical order and just showed names and other information about files, but not their contents
* some web servers would look for a special file named `index.html` and if it was present, would serve that file instead of the index
* these days, most web servers don't show any indexes at all, ever...
* ...but the default page for a directory is still named **index**.html
* This is *why* index.html is named *index* -- it is a *replacement* for the automatic default *index* page.

Now open a web browser and visit <http://localhost:5000/> and you will see the contents of `index.html` ("Hello in HTML") even though your request did not contain the words "index" or "html", just the path `/`

---

# Content-Type

* files on disk usually have *extensions* that tell you what file type they are
    * `.html` or `.htm` means HTML
    * `.js` means JavaScript
    * `.css` means CSS Stylesheet
    * etc.

* but URLs often *do not* have extensions
    * `https://developer.mozilla.org/en-US/docs/Web/JavaScript` is an HTML page but *does not* end in `.html`

* so web servers must read the file type extension and then use the `Content-Type` HTTP header to tell the client what format the file is in
    * `text/html` means HTML
    * `application/javascript` means JavaScript
    * `text/css` means CSS Stylesheet
    * ...these are called *MIME Types* (after the Multipurpose Internet Mail Extensions specification)

---

# Viewing Headers

**TIP:** open the browser DevTools and click on the Headers sub-tab to see Content-Type and other headers:

![headers](/images/content-type.png)

---

# Match the Route not the Path

When setting up our links on the front end we want to match the routes we set up on the server, not the actual path to the file.

This will allow us to more accurately define our site structure so it's representative of the purpose of our pages rather than being bound to the physical location on disk.
