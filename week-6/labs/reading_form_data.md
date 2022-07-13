# Reading Forms on the Server

## Welcome!

The purpose of this lab is to get more comfortable reading form data on the server. In this lab we will be creating a Madlibs style game where we will ask the user for a few words, and then enter them into a story when the final word has been submitted; using forms! We will be setting up dynamic routes to ask the user for words in sequence until we have enough words to fill out our story.

## Initializing the project

* Create a new directory named `mad-server` and `cd` into it
* Get it ready to install packages with `npm init -y`
* install `express`
* create a `public` folder

## Building the Front End

Inside your `public` folder create an `index.html` file and add a title, a prompt ("are you ready to begin?") and at least one button.

When the button is clicked it should link to the route `"/first-word"`

Feel free to style this page, and play around with the layout so that it looks nice!

## Setting up the Server

Set up Express by:

* Importing the package using the `require` function
* Initializing the express app by calling `express` and assigning it to a variable
* Setting up the `.listen` method to listen over a port
  * I will be using port 5000 as an example, but any number over 1048 should work fine

Since we will be dealing with a lot of forms in this lab we will want to include some middleware to make reading URL encoded post bodies easier to read. We can use the `express.urlencoded` middleware to help with this, and use it on every route by calling `app.use` and passing it in.

```js
app.use(express.urlencoded({extended: true}))
```

> The argument to `.urlencoded` is an *options object* and we will get a warning in the console without it.

You should also set up a route listening for a `get` request at the path `"/first-word"` that sends the result of form inputs as it's response. The form should have a `method` property assigned to `"POST"` and an action of `"/second-word"`. This form should also contain a text input with a `name` property assigned to whatever type of word it is (adjective, noun, verb, etc.), and a submit button. For example purposes I will assume the input has a name of `noun`

You should feel free to send this form over either by creating it on the server and sending it via a `.send` method, or by creating an HTML file in the public directory that contains this form, and sending that over with the `.sendFile` method. It would also improve the user experience to set a placeholder value on your text input saying what type of word you expect, and/or a label for that input.

## POST vs GET

Since we are using this form to send data to the server we send it via a `POST` request rather than a `GET` request since that will be a little bit easier to deal with (and doesn't clutter up our URL with query parameters).

Set up a route to handle a `post` request coming in along the path `"/second-word"`

## View the Request Body

Because we are using the `express.urlencoded` middleware on all of our routes, any route that responds to a `POST` request has access to that request's `body` property. In the case of a post request from a form the `body` will be the data entered into the form as a JavaScript object with keys equal to the name properties on your inputs, and values being whatever the value property of that input was at the time of submission.

Go ahead and see what you're getting from your form by `console.log`ing the `request.body` in the request/response handler you set up for the `POST "/second-word"` route.

## Building the Story

While *client side* JavaScript transformations are lost when a page refreshes, redirects, or is otherwise reloaded, *server side* JavaScript **persits** until the server. Since this is a fairly small application that will only need to store a few strings we can store our form responses as *global variables on the server*. This does mean you'll need to initialize some global variables at the top level of your server, and reassign them to the value of your form submissions inside your request/response handlers (this would be `request.body.noun` for that first form.)

Once you've reassigned the variable send another form as the response. This form should also have a `method` of `"POST"` and an `action` of `"/third-word"`

Set up a route handler for the post request from that form, that reassigns a different variable, and sends another form as it's response.

Continue this pattern until you have at least 5 words for your story.

## Redirects

For the final form instead of sending another form as the response after reassigning a variable let's do a redirect to the path `"/story"`.

Redirects send `GET` requests to the specified URL and are done from inside a request/response handler function in Express like so:

```js
response.redirect("/")
```

The above redirect would send you back to the homepage (which is not where we want to go in this case...)

## Telling the Story

When you `GET` the path `"/story"` on the server we want to send back our full Madlibs story as the response. It will probably be easiest to generate this story on the server side and send it over using the `.send` method rather than creating an HTML file for your story.

The story page should also contain a button that when clicked:

* Resets the variables on your form that stor your words
* redirects you back to the homepage

## Celebrate!

Run through the game a few times with your classmates. Have fun with it!
