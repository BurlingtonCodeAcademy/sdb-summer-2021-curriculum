# Passing Data

## Welcome!

In this lab we will be looking at how we can use the URL to send data to programs, and pass information between different web pages. To do this we will be building a form that allows you to set a number of names, and then redirects you to a page that greats everyone in the party.

Create a new directory with two html files, one for your home page, which should be named `index.html` and one that we will use to display a greeting to your users, which I will refer to as `greeting.html`. Each of these pages should have a linked JS file.

In `index.html` create a form that a user can type their name into. We'll be expanding this form later, but for now it only needs a single input field.

## Reading URLs

Every URL is made of several parts. The protocol, and domain name make up the heart of the URL, and those are what we mostly see when surfing the web. Together they make up the address of the page, and look like this: `http://www.example.com/path`

In general those parts of the URL tell your browser what computer to look on, and which file to look for to show you the website. They are responsible for navigation on the web. There are other parts of the URL which can be used to pass data, usually to determine what to show on the page, such as search results. These parts are the hash, and the query.

## The Hash

The Hash was originally designed for *internal navigation*. It was designed to be used as an href value to jump to a section of the current page.

If you want to try out this functionality go ahead and generate a block of lorem ipsum text below your nav bar. The goal is to make the page scrollable so that you can jump to a different section of it, so don't be stingy with the text! Below the text add an element to use as a target. Any element will do, but we'll need to give it an id. If we use an empty `div` and give it an id of "bottom" we can use it as the target of our link, and nothing will appear on the page. Go back to the nav bar, and add an anchor tag with an href equal to a hash and the id of your target. `<a href="#bottom">Jump to Bottom</a>` will create a clickable link that will jump to the element `<div id="bottom"></div>`. Don't forget to put some text in your anchor tag, otherwise you'll have nothing to click on.

Because the hash doesn't change or reload our page we can also use it to send messages to a JavaScript program. Be aware that if there is an ID on the page that matches the hash you will jump to that section of the page!

## Reading the Hash

We can access the hash (or any part of the URL) in JavaScript through the `document` object

In your JavaScript file `console.log` the `document.location.hash`

Add a hash to your URL in the browser and hit enter

Look at the your browser's console to see what the value of that hash property is. Notice how it has that "#" at the beginning? We probably don't want that

## Strings Never go Away

Think back to the first week. How could we *slice* off just the part of the string we want? What index number is the *first* character at?

## Redirecting

To do a redirect in JavaScript we can reassign the `document.location` property to the new path we want to go to. So to go to the "greeting" page we can reassign our location to that path, and attach a hash mark, and the user name that was entered in the form like so: `document.location = "/greeting.html#" + userName`

This will allow us to transfer the name between pages.

* In the JS file for the `index.html` page create an event handler for your form
* when the form is submitted read the value of the name that was entered, and redirect to the "Greeting" page, passing that name as a hash
* On the greeting page, read the hash, and create a custom greeting using that name

## The Query

Hashes are great if we need to send a single piece of information, but they don't handle passing sets of data very well. If we need to send over a more complex data structure with the URL we should probably use a query parameter.

The query parameter is set with a question mark `?`, and consists of key/value pairs defined with equals signs `=`, and separated by ampersands `&`. We can access the query parameter in JS by using `document.location.search`
