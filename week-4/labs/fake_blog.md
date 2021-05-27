# Mock Blog

## Welcome!

In this lab you will create a blog front end with users, and posts pulled from jsonplaceholder.typicode.com containing several different sections:

* A home page
* An author page
* And a blog post page

* On the home page there should be a sidebar with a list of authors
* When an author's name is clicked it should send you to a page with all the posts by that author.
* On the homepage there should be a list of all blog posts, displayed by title
* When a post is clicked it should take you to a dedicated page for that post with the author's name, the title of the post, and the body of the post formatted nicely on the page.

> Hint: Create template pages for authors and posts, then use query parameters, or url fragments to determine what data to fetch. This will make it so you don't need 100 very similar pages for each post.

## Creating the Pages

Before we start building out the functionality for our site we need to set up the site's architecture.  Create 3 html pages that correspond to the 3 different views on our site; `index.html`, `author.html`, and `post.html`

We will also want to add some styling to each of these pages. There are two competing opinions in web design about how to organize your styles. Having a master CSS file that contains all the styling for your site, or having a dedicated CSS file for each page. Use the method that feels most comfortable to you. If you do decide to have a master CSS file it is important that you structure the file in a logical manner to make different sections, and page specific styles easy to find.

Because we want each page to have different functionality we should also create a dedicated JavaScript file for each page.  Create a "script" subdirectory with 3 JS files in them named `index.js`, `author.js`, and `post.js`

You should also create a wire frame for each page to roughly outline how you want the content laid out.

## Fetching JSON

On the home page we want 2 lists. One with all the authors, and another with all the available posts. To get this data we will need to [fetch](/lessons/slides/fetching-and-AJAX) it from an API so we can load it into the page. We'll be using [JSON Placeholder](http://jsonplaceholder.typicode.com/) as our endpoint to fetch the mock data.

To get the list of all the authors we'll want to fetch from http://jsonplaceholder.typicode.com/users

To get the list of all posts we'll want to fetch from http://jsonplaceholder.typicode.com/posts

**Visit these locations in your browser *first* to see what the data you're fetching will look like!**

Then bring them into your JavaScript files by using the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

> Remember: You will need to chain two `.then`s off of your fetch to properly parse the data

## JSON Collections

Both of these endpoints serve a JSON Collection, rather than a single JSON object.  You might notice that the JSON Collection looks a lot like an array of objects.

When you bring a JSON collection into JavaScript you can use it just like a normal array.

We're going to want to do something *for each* object in the collection, so let's iterate over the collection, just like we would with a normal array!

## Working with JSON

JSON objects are just JavaScript Objects, and we can access their properties in exactly the same ways.

When we're fetching any data we can only use it from inside of the second `.then` because of the ways callbacks, and promises work. Once you're in a promise chain

We don't want to put our JSON objects on the page as is, that would look pretty bad. Try `console.log`ing each object to see the available properties, and extract just the values you need.

## Creating Elements

Now that we have the information we want to put on the page (the author's names, and the post titles). We will need to do this from inside our promise chain, since that is where our data is. More specifically we'll need to write the majority of our code inside the callback function in the second `.then`

We can create new elements using `document.createElement` and passing in the type of element we want to create. Since we are building linkable lists of authors, and titles an `a` element wouldn't be a bad choice. We'll need to assign the call to `document.createElement` to a variable so that we can reference it later on.

To insert text into the element we just created we can manipulate its properties. By assigning the `.textContent` property of the element we just created to the author's name, or the post's title we can put that text into that element.

To set up links to the appropriate page we'll also need to add an `href` property. This should be equal to the page you want to link to and an identifier. IDs tend to make good identifiers because they are generally unique for each entry.

The href for or blog post titles might look something like this: `"/post.html#" + postData.id`

## Appending Elements

To put elements on a web page we will first need a location to put them. If you haven't already, create some container elements on your page to put your lists of author names, and post titles in. Use DOM queries to target those containers, and store them in variables for later use.

we can use the `.appendChild` method to add child elements to our HTML in JavaScript. If we target our container elements, and call `.appendChild` on them, passing in the element we just created as our argument it will put the element on the page.

## Template Pages

We don't want to have to create 100 very similar pages for every post so instead we're going to have our 

What endpoint do we need to fetch from to get an individual post from json placeholder? Visit the site, and figure it out!

We'll talk about URLs, and how to use them to pass data a little later on. For now we're going to use a URL fragment to pass data. URL fragments are always at the end of the URL, and are marked with a hash `#`. We can access them using `document.location.hash`

* `www.example.com/location#data` is a URL with the *path* "/location" and the *hash* "#data"
* Hashes are useful because they don't change where the path routes to

## Mapping Data

If you look at the post objects you might notice that they don't contain the author's name. How could we get the Author's name using the data contained within the post object?

Now build out the author page. Remember to check what data is available to you, and think about how we could sort our collection of posts based on that data.

## Adding Style

Add some rudimentary styles to lay out the pages, and make them look nice. Set your home page up with the titles of all the posts as the main content, and the authors in a side bar. Style the Author page so that the Author's name is readily apparent, and the article titles are listed below it. Make the post look like a nicely formatted blog post with a bold, underlined title, and the italicize the author's name. Feel free to get creative, and have fun with it!
