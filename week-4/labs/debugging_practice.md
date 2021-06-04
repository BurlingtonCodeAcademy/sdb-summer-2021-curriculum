## Debugging Practice

## Welcome!

The goal for this lab is to help you get comfortable debugging things in the browser. To that end I've built a little example website which is, unfortunately, a bit broken. See if you can debug the site, and get it displaying, and functioning properly.

## Site Design

![working site screenshot](https://res.cloudinary.com/btvca/image/upload/v1622826263/curriculum/markdown-preview-complete_maogb8.png)

## Site Functionality

This site is a markdown preview site. Markdown is a shorthand way of writing HTML, and is commonly used in blogs, and forums. You may have even written markdown at some point without oven knowing it! It's very common to allow markdown on forums, or blogs to allow users to style their posts.

This site contains a typeable text field, and a display area. When you type markdown text into the display area it should be rendered as HTML in the preview area in real time.

## Markdown

Markdown is 100% text based with different characters representing different HTML tags

* `#` creates h1s, `##` creates h2s, and you can keep going with this pattern all the way to h6
* Surrounding text with `*` italicizes while `**` makes it bold
* `*` as the first character on a line creates an unordered list, so does `-`
* Numbers at the start of a line create ordered lists
* and much more...

## Clone Down the Starter Code

There is a template repo with some starter code you can clone down [here](https://github.com/BurlingtonCodeAcademy/dom-debugging-practice-lab).

While the site is intentionally broken, There is nothing wrong with the import, or usage of the "marked" function, and there are also no errors in the CSS itself.

## Viewing the Page

Once you've cloned the repo down, `cd` into it, and run LiveServer. This should allow you to view the page on http://localhost:5500. Since LiveServer does "hot reloading" you can leave LiveServer running, and as you make changes to the page you should see those changes reflected in the browser.

## Inspecting the Page

You might notice that the page doesn't look quite like the screenshot above. Let's figure out why!

If you inspect the page, and look at the various elements you can see that none of the styles in our `index.css` file are being brought in. Why do you think that is?

Go back to the code, and find where we're importing our stylesheet. Is our import link missing anything?

## The "Sources" or "Debugger" Tab

If we go back to the browser, inspect the page, and go to the "Sources" tab in Chrome, or the "Debugger" tab in FireFox we can actually see which files are being served at 127.0.0.1:5500 (localhost:5500). If you haven't changed anything in the HTML we can see that the only thing being served is our `index.html` file. That's why our styles aren't being applied, they're not being loaded in the first place! We want to be serving 3 files; the `index.html`, our styles, and our scripts.

Go back and read the HTML code. What is missing? How can we bring in our styles, and scripts?

## The "Network" Tab

We can also look at the "Network" tab to see what files are being used by the site. The network tab gives you more information about the way the files are being loaded into the site, such as their response status, expected file type, size, and how long it takes to load into the site. The "Sources" or "Debugger" tab will allow you to preview the file's contents, though it will give you less metadata about how the files are loaded in.

## The Console in the Browser

Once we've got all our files loading in properly the site should look a bit better, but the functionality still won't be there. At this point our CSS, and HTML are fine so we're on to debugging the JavaScript. One of the most useful tools you have as a developer is the console. In the browser we want to access the *browser's console, not our terminal*. We can do this by inspecting the page, and opening the "Console" tab.

Are we getting any error messages? Read the error, and figure out where it's coming from. What is the `source` variable? What do we expect it to be? How are we using it in our code? Where is it defined?

As you fix one bug you will reveal more bugs. This is a normal part of the process, and you shouldn't get discouraged. If you're getting different error messages, that's progress! If you change something, and the error message stays the same you've just eliminated a possible cause of the bug! Remember, not all bugs cause errors, some just make the program behave ...oddly. These tend to be the hardest bugs to fix.