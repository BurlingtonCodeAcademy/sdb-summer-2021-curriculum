# Image Gallery

## Welcome!

The purpose of this lab is to get a little more comfortable with grid by making a responsive gallery of thumbnail images. Lets first start by creating an HTML file and a CSS file that is linked to the HTML file

Here's a [great Grid guide.](https://css-tricks.com/snippets/css/complete-guide-grid/)

## Wireframe

Try drawing out your own wireframe that includes the following elements:

- A title, centered on the top of the page
- 20 image thumbnails in a 4x5 grid
- Each thumbnail should be the same size
    - and fit entirely in it's grid cell.

## Block Out the Content

Block out the main sections of your page as drawn in your wireframe.

- Try to consider which elements need to be in each section.

- Try to put things in the general order you want them to appear on the page.

## Placeholder Images

Here are some sites that we can use for free placeholder images:

- [fillMurray](http://www.fillmurray.com/)
- [placeCage](https://www.placecage.com/)
- [placeKitten](https://placekitten.com/)
- [placeBeard](https://placebeard.it/)
- [loremFlickr](https://loremflickr.com/)

## Create the Grid Container and its layout

Creating a grid container defines the element as a container and establishes a new grid formatting context for its contents.

The 4 most important steps to setting up a grid container and its layout

1. Create the grid container element and declare its display as grid

```css
.container {
    display: grid;
}
```

2. Within that container element, define its tracks use grid-template properties
3. Place child elements _within_ the container
4. Specify the gaps with grid gap properties

## Making it Responsive

CSS Grid was built with responsiveness in mind so lets make the image gallery responsive!
You won't even need media queries!

[Here's a good guide for making your grid responsive.](https://css-tricks.com/look-ma-no-media-queries-responsive-layouts-using-css-grid/)
