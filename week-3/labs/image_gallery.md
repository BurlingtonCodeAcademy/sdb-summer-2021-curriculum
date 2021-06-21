# Image Gallery

## Welcome!

The purpose of this lab is to get a little more comfortable with grid by making a responsive gallery of thumbnail images. Lets first start by creating an HTML file and a CSS file that is linked to the HTML file

[usefulTips](https://css-tricks.com/snippets/css/complete-guide-grid/)

## Wireframe

Lets work with a 3x3 image gallery and create a wireframe of how the page will look in the end.

## Block Out the Content

Build the wirefram inside the <body> of the html page

## Placeholder Images

Here are some sites that will give free images to use as placeholder images:
- [fillMurray](http://www.fillmurray.com/)
- [placeCage](https://www.placecage.com/)
- [placeKitten](https://placekitten.com/)
- [placeBeard](https://placebeard.it/)
- [loremFlickr](https://loremflickr.com/)

## Create the Grid Container and its layout

Creating a grid container defines the element as a container and establishes a new grid formatting context for its contents.

The 4 most important steps to setting up a grid conatiner and its layout
1. Create the grid container element and declare its display as grid
```
.container {
    display: grid;
}
```
2. Within that container element, define its tracks use grid-template properties
3. Place child elements _within_ the container
4. Specify the gaps with grid gap properties

## Making it Responsive
CSS Grid was built with responsiveness in mind so lets make the image gallery responsive!
You won't need media queries
[responsiveGrid](https://css-tricks.com/look-ma-no-media-queries-responsive-layouts-using-css-grid/)
