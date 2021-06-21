# Image Wrapping

## Welcome!

In this lab we will be playing around with floats to do text some wrapping around images, and a simple 2 column layout

In a new subdirectory create a new `index.html` file

## Wireframe

![Two column wireframe](https://res.cloudinary.com/btvca/image/upload/v1624230990/floating-img-wireframe_xjqf2g.png)

## Create an Outline

The easiest way to start creating a page is to block out the main sections you will need, then fill in the content, and finally style the page a section at a time.

For this page we're going to want a *header* section which will contain our page's title, and a *main* section that will contain 2 articles which we will eventually stack side-by-side.

## Fill in Content

* In your header add a title to the page. Make it big, and bold.

* Each article will need an image, and some text. 500 words of lorem ipsum should be sufficient for the text, though you should feel free to add more.

* Your images shouldn't be much more than 300px wide

## Style Your Page

There are several ways to attach styles to your web page. The most straightforward, but least organized way of doing so would be to add a `<style>` tag to your HTML

If you want to keep things a bit more organized you can create a separate CSS file and link it to your page

* through a `<link>` tag with an `href` property pointing to your CSS file, and a `rel=stylesheet` property
* through a `<style>` tag with an `@import` statement pointing to your CSS file

Use your styles to apply the following changes to the html:

* center the title
* wrap the text around the images in your articles
* Put the articles side by side, with a little space between them, and even distance from each edge

Check the wireframe for a (rough) visual representation of the desired page layout.
