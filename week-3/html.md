# Intro to HTML

* HTML stands for Hyper-Text Markup Language
* Every HTML file is one web page
* Invented by Sir Tim Berners-Lee
* Based on SGML
* Standard language used for creating web pages
* Composed of tags
* CSS and JavaScript are designed to work in tandem with HTML
* HTML is for structuring content

# What Is It?

HTML is a coding language composed of various types of *tags*, also known as *elements*. These are what are used to build web pages.

* HTML is used to **build** web pages by using **tags**.
* Web browsers "read" HTML and render it as pretty visual elements for humans.

---

# Standard Page Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My House</title>
  </head>
  <body>
    <p>My house is a very very very fine
     house, with two cats in the yard.</p>
    <p>Life used to be <strong>so
     hard</strong>; now everything is
     easy 'cause of you.</p>
  </body>
</html>
```

---

# Elements (aka Tags)

Lets break down the page structure above. You can see above, all HTML tags are surrounded by angle brackets. You can also see that every tag has what is known as a **closing tag**. These are the tags that have a preceding forward slash. For the most part, every HTML tag needs to have a closing tag.

---

# Examples of Structural Tags (Layout)

| tag      | meaning                   |
|----------|---------------------------|
| `<head>`  | head (contains metadata)  |
| `<body>`  | page body                 |
| `<div>`   | division                  |
| `<h1>`    | Heading (level 1)         |
| `<p>`     | Paragraph containing text |
| `<span>`  | Text without a line break |
| `<img>`   | Image tag                 |

---

# Examples of Style Tags

| tag                  | example                         |
|----------------------|---------------------------------|
| `<b>`                 | <b>bold</b>                     |
| `<i>`                 | <i>italic</i>                   |
| `<strong>`            | <strong>strong</strong>         |
| `<em>`                | <em>emphasis</em>               |
| `<br>`                | Line break                      |
| `<hr>`                | Horizontal rule (dividing line) |
| `<blockquote>`        | "call-out" quotation            |
| etc.                 |                                 |

---

# Self Closing Tags

Some tags can act as both an opening and a closing tag. These are written with a forward slash at the end, and are most commonly seen for tags that insert something into the page such as an image, or a line break. e.g. `<img src="myImg.jpg" />` is a self closing image tag.

---

# Attributes

Attributes further define HTML elements and their purpose. For example, an image tag may have the following attributes:

```html
<img src="/images/cat-pic.jpg" title="Cat Picture" alt="Picture of a fuzzy cat">
```

* `src` defines where the image file is located.
* `alt` is alternative text to be displayed if the image cannot be.
* Attributes are not always required. However in the example above, a source is needed for the image to be displayed.
* Others include `style` (for inline CSS), `title` (for hover-over tooltips), `href` (hyperlink reference)
* Attribute names should always be lowercase

---

# Style vs Layout vs Semantics

This war has raged inside HTML since the beginning of the web.

Some tags exclusively describe _how_ it's contents should be displayed (ex. `<b>`), where as some _describe_ it's contents (ex. `<strong>`). Web content isn't just about appearence. It matters how it is intepreted.

* Semantics are all about meaning - what is the purpose?
* Not all HTML elements convey meaning - not all HTML elements are semantic (e.g. `div`).
* Imagine a blind person using a screen reader - how might they understand the difference between a `<strong>` and a `<b>` tag?
* Not all elements **style** content, and not all elements define **structure** or layout.

---

# HTML Has Flaws

* Difficult to parse (both for humans and for programs)
* Poor whitespace rules
* Case insensitive, except when it's not
  * For example, Ç is &amp;Ccedil; and ç is &amp;ccedil;
* Open and close tag names should match but often aren't required to
  * For example, &lt;b>bold &lt;i>italic&lt;/b>&lt;/i>
* Browsers will happily render invalid HTML, which leads to the propagation of invalid HTML
* Muddled distinctions
  * between *semantics* (what the tag's content *means*) and *style* (how the tag's content is *displayed*)
  * between *elements* and *attributes* and *content*

---

# Proper HTML5 Web Page Structure

Remember how we discussed semantic HTML? Well in modern day HTML there are a number of elements that help to semantically structure and lay out the content on your website.

![Image of HTML5 page structure](https://i.pinimg.com/originals/46/e2/1c/46e21c46e7001fca6554cd45562268fa.jpg "HTML Page Structure")

---

# What To Know About These Tags

* Not all of these elements *have* to be used. 
* Each is meant to contain a specific type of content. In fact, you do not need to use any of these.
* They help screen readers and search engines to determine the structure of your website, and help to achieve higher SEO rankings. You could simply replace all of these HTML5 tags with `<div>` tags
* Using these tags **will not automatically layout your page** as shown in the previous image. They simply help to *describe* what the content is on your website. Browsers render them all the same as a `<div>` element.
