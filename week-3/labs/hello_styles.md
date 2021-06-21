# Hello Styles

## Welcome!

In this lab we'll be going back to our hello-html lab, and sprucing up the page by adding some styles. Currently you should have a header at the top of the page that has a title saying something like "Home Page," a nav bar just below that, with a link to the "About" page, and a main section below that, which has a picture sitting on top of some text.

The idea here is take this page, and style it so that it looks like the page below. If you want to use your own typography, colors, and images feel free to add your own flair. Get creative with it!

## Site Wireframe

![site wireframe](https://res.cloudinary.com/btvca/image/upload/v1624232231/hello-styles_pprhzq.png)

## Linking Styles

Before we start styling our page, we'll want to create a stylesheet and structure our directory so it's nice and organized. As a general rule of thumb we want different code languages to be in dedicated files, and we want different files types in dedicated subdirectories. This makes it easier for you, and other programmers to find the code they need.

* Inside "hello-html" create a subdirectory called "styles"
* Inside "styles" make a file named "styles.css"
* To link your styles to your webpage go back to your "index.html" file and add a `<link>` tag with an `href` property, and a `rel` property
  * the `href` should point to the *relative filepath for your css file*: `href="/styles/styles.css"`
  * the `rel` tells your html what type of file to expect. For CSS it should be `rel="stylesheet"`

## Adding More Sections

If we look back at the example screenshot above we can see that there's another article, and image in our main section.

Create another section in the main section of your html for these elements.

## A Brief Introduction to Floats

We can use a `float` property in our css to cause text to wrap around images. We will be covering floats in much more detail later, but for now target your first image tag in your CSS and apply the style `float: left`

This should cause the image to align on the left side of the page, and allow the text to wrap around it. Add more placeholder text if there's not quite enough to wrap below the image.

## Targeting Your Elements

You may find that to duplicate the layout from above you need to be more specific than just targeting by tags

You should feel free to add classes, and ids to any elements you need to target directly.

## Applying Styles

Apply styling to your HTML so that:

* The title has multiple colors, and is a different font than the rest of the page
* The link in the nav bar changes color when you hover over it
* The first image is flush against the left side of the page, with the text wrapping around it
* The second image is below the first section, and flush against the right side of the page with text wrapping around it
* The title, nav bar, and main sections should all have different background colors, and the text should still be legible for all of the,

## Inherent Styles

Some elements have *inherent styles* which are applied by default. They can always be overwritten in your CSS, but might cause some layout issues if you're not expecting them.

You may notice a white border around your page. This is because the `body` element inherently has an 8px margin all the way around. You can remove this by targeting the `body` and setting `margin` and `padding` to `0`
