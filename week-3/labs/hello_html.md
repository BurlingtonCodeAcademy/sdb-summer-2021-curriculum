# Hello HTML!

## Welcome!

In this lab we will be building out a website using HTML. Ultimately we want it to have the same basic layout of the rough wireframe below, but for now let's focus on getting the content on the page!

![Hello HTML Wireframe]()

Create a file named `index.html`. The name `index.html` is actually significant, and your homepage should **always** be named `index.html`.

## Using Emmet Abbreviations

When we're in VSCode we have access to a Emmet Abbreviations which are certain key combinations that auto-fill content. To create an empty HTML template you can type an exclamation point `!` and then hit the <kbd>Tab</kbd> key in any HTML file.

## Let's Add Content!

We will now add some text to our first web page! Inside of the `<body>` tag, let's add the following text:

```
Hello, world!
```

So it looks something like this:
```html
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    Hello, world!
  </body>
</html>
```

> *Don't worry if there's more content in the `head` of your document. That's just metadata about your page, and it' better to have it than not*

## Use a VSCode Extension to View the Page

There are several plugins for VSCode designed to help you serve static webfiles. Let's use one to make viewing our webpage a little easier.

* Go ahead and click the "Extensions" (or press <kbd>ctrl</kbd> + <kbd>shift</kbd> + X)
* Search for 'Live Server' and install the extension of that name developed by Ritwick Dey.
* Close and reopen VSCode.
* You should now have a button in the lower right corner of VSCode that says 'go live'
* Click it to launch your site (locally at least)

## Inspect The File With Chrome

* In your browser, open the "Developer Tools" window
  * On Mac - `⌘ + Shift + C`
  * On Windows / Linux - `Ctrl + Shift + C` or `F12`
  * Or: *right click* on the page and select 'inspect'
* If it isn't clear, find and click on the elements tab
* Notice how the HTML tags are displayed
* You can do this for **any website** to examine how it is structured
  * or to change its colors, or remove ads, etc...
  * Note that this only changes the page for you, and only while you're on that page. Refreshing the page will clear all changes.

## Block Out the Sections

Let's start laying out our web page. HTML tags will stack on top of each other so the first step to laying out our webpage is to block out our main sections *in the order we want them to appear on the page*.

We're going to need a *header* section, a *nav* section, and a section for our *main* content. You could use *div* tags to represent these, but [more modern HTML5 tags](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#content_sectioning) will be more accessible, and more readable for both humans and bots.

## Add Content

In the header section add a title that says something along the lines of "Home Page"

In your navigation section add a single anchor tag that we will use to link to the about page. Don't forget to put some text in it, or nothing will show up!

In the main section add an image, and some text

## Lorem Ipsum

You can easily generate placeholder text by using *lorem ipsum* which is ungrammatical latin dummy text often used to mock out content. The emmet abbreviation for generating lorem ipsum text is the word "lorem" followed by the number of words you need. e.g. if you typed `lorem250` and then hit <kbd>Tab</kbd> you would get 250 words of placeholder text.

There are also many different [lorem ipsum generators](https://loremipsum.io/ultimate-list-of-lorem-ipsum-generators/) you can use to spice up your placeholder text. Try a few out, and have fun with it!

## Linking Pages

To link multiple pages together we will first need to make another page. In the same directory that your `index.html` file lives in create a new file called `about.html`. Create a shell for your html file and add a heading to the page.

To link to the about page from the home page you will need to add an *href* to the `<a>` tag in your nav bar:

`<a href="/about.html">About</a>`

Clicking the word "About" in your browser should take you to the about page.

Add a link on the about page that will take you back to the home page as well.

> Linking to just "/" should take you back to the home page.

## Going Further: Styling the Page

To add some simple styles to your page you can use a `<style>` tag, and then write some CSS to modify the way certain tags are displayed on the page. We will be covering CSS in much greater depth later this week, but if you want to spruce up your page a bit you can reference [this documentation](https://developer.mozilla.org/en-US/docs/Web/CSS) and start playing around with some of the basic concepts.