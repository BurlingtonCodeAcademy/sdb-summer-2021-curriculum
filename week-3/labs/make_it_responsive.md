# Shift It Around

## Welcome!

In this lab we will be going back to the code we wrote for our Floating Images lab, and modifying it so our site will be fully mobile responsive

We have a page that is starting to look somewhat decent, but what happens when you squish the screen down?

## Using Media Queries

Media queries are used to specify different styles to apply under certain conditions such as different screen sizes, or views.

You can set up a media query with the `@media` expression followed by a condition in parentheses, and a new style-set between curly braces:

```css
@media (some_condition) {
  p {
    /*Some style changes*/
  }

  .some-class-name {
    /*More style adjustments*/
  }
}
```

The new style sets inside your media query will *overwrite* any matching styles assigned in your main CSS, but will preserve all of the other CSS styles.

## Before you Start

Try drawing out a simple wireframe for your mobile view. Think about how your content can be presented so it still feels familiar, but is viewable on a mobile device.

## Change the Styles

Feel free to alter your layout to use flexbox and/or grid instead of floats while you complete the following tasks for mobile view (screen width < 450px). Here are a few guidelines for laying out your content in a mobile view:

* Don't wrap the text around the images
* Stack the articles rather than laying them out side-by-side
* Decrease the space between elements
* Resize the images so they fit the page.
