# Best practices

When setting up flexboxes and grids here are a couple things to keep in mind:

* While grids and flexboxes can be used to alter the natural flow of your HTML, it's better to use them to *enhance* it instead
* Using semantic HTML prevents `div`itis -- using too many `div`s within `div`s within `div`s within `div`s.
  * Rule of 3: Try to not nest anything more than 3 levels deep.
* Use the layout of the DOM *first* and flexbox/grid to *adapt* that natural flow when needed.
  * Add flexboxes, and/or grids *only where necessary*
  * Keeps your work clean and easier to edit/debug

---

# Which to Use When

Flexboxes are best used to align things in a single direction such as:

* nav bars
* drop down menus
* lists
* sidebars
* headers

Grids are best used for laying out things in two dimensions, such as:

* full page layouts
* complex footers
* contact forms
* image galleries

---

# Nested Flex Boxes and Grids

You can nest flex boxes inside other flex boxes, or inside grids, and the same is true of nesting grids.

While this can be very useful for setting up more complicated layouts keep in mind:

* Grids, and flexboxes both only operate on their *direct children*
  * So your parent grid or flexbox container will be aligning the flexbox *containers* inside itself which will be responsible for their own items
* When using nested grids or flexboxes you are *by necessity* at least 3 levels of nesting deep for the items inside your nested flexbox or grid.
  * This can get very confusing very fast.

---

# Why Would We Do This?

What do you think? There are no wrong answers here...

---

# Because...

You may need to set up a more complicated layout for your items inside something like a side bar.

e.g. If you have a sidebar that has a list of article previews you might want to make the sidebar a flexbox with `flex-direction: column` to easily mange alignment, and justification of the article previews.

You might then want to make the article previews flexboxes if they contain a title, preview image, and a short description to manage the layout of each article preview.
