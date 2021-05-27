# Passing Data

## Welcome!

In this lab we will be looking at how we can use the URL to send data to programs, and pass information between different web pages. To do this we will be building a form that allows you to set a number of names, and then redirects you to a page that greats everyone in the party.

Create a new directory 

## Reading URLs

Every URL is made of several parts. The protocol, and domain name make up the heart of the URL, and those are what we mostly see when surfing the web. Together they make up the address of the page, and look like this: `http://www.example.com/path`

In general those parts of the URL tell your browser what computer to look on, and which file to look for to show you the website. They are responsible for navigation on the web. There are other parts of the URL which can be used to pass data, usually to determine what to show on the page, such as search results. These parts are the hash, and the query.

## Redirecting

# Window Methods

## The Hash

The Hash was originally designed for *internal navigation*. It was designed to be used as an href value to jump to a section of the current page.

If you want to try out this functionality go ahead and generate a block of lorem ipsum text below your nav bar. The goal is to make the page scrollable so that you can jump to a different section of it, so don't be stingy with the text! Below the text add an element to use as a target. Any element will do, but we'll need to give it an id. If we use an empty `div` and give it an id of "bottom" we can use it as the target of our link, and nothing will appear on the page. Go back to the nav bar, and add an anchor tag with an href equal to a hash and the id of your target. `<a href="#bottom">Jump to Bottom</a>` will create a clickable link that will jump to the element `<div id="bottom"></div>`. Don't forget to put some text in your anchor tag, otherwise you'll have nothing to click on.

Because the hash doesn't change or reload our page we can also use it to send messages to a JavaScript program. Be aware that if there is an ID on the page that matches the hash you will jump to that section of the page!

## Reading the Hash

We can access the hash (or any part of the URL) in JavaScript through the `document` object

`document.location.hash`

Take a look at it. Look at it!

Notice how it has that "#" at the beginning? We probably don't want that

## Add the Hash to the Redirect

## Strings Never go Away

Think back to the first week. How could we *slice* off just the part of the string we want? What index number is the *first* character at?

## The Query

