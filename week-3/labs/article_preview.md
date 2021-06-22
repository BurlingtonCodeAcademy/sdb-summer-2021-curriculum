# Article Preview

## Welcome!
​
The purpose of this lab is to get a little bit more comfortable using flexbox, and nested flexboxes, by creating a blog-style site layout with a main article displayed on the page, and a sidebar that contains a list of other articles with titles, preview images, and a short text description
​
## Wireframe

Draw a sketch that breaks down the layout of your blog-style site.

Here's one example of how it could be drawn, but feel free to sketch out your own, and design a site that looks good to you. It must contain:

* A title at the top of the page that spans the full width of the page
* A sidebar containing several article previews
  * Each preview should contain a title, small thumbnail image, and a little bit of text
* A main article with a title, author, and optionally a large image

![Wireframe example](https://res.cloudinary.com/btvca/image/upload/v1624313532/wireframe_psscfs.png)
​

## Block out your elements

Then, using your sketch, draw a box around content that you want grouped (and therefore manipulated) together. Draw a box around what elements will be nested within your larger boxed out content.

![Blockout Example](https://res.cloudinary.com/btvca/image/upload/v1624313569/blockout4_imo8r0.png)
​

## Start Big

Using your wireframe, fill in content by creating the html elements that correspond to each box that you blocked out.

- Make all of your largest boxes first, not concerning yourself with the elements within just yet.
- Use CSS flexbox properties to adjust elements to mirror your wireframe.
  For example:
  ​

```css
.container {
  display: flex;
  flex-direction: column;
}
```

## Work Your Way Down

After the site's largest parts, you can go ahead and add the smaller html elements nested within. These would include more granular tags such as article headings, body tags, images, or captions.
​
## Adjusting Alignment and Spacing

Lastly, adjust your elements within your larger html elements so that they also match your wireframe. Make changes as needed to all elements to adjust alignment and spacing. Helpful CSS flexbox properties include `align-items`, `align-content`, and `align-self`.
​
# Resources

[Everyone's favorite Flexbox Helper!](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
