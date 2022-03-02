# Mock Blog

## Objective

In this lab you will create a fake blog with users and posts pulled from <jsonplaceholder.typicode.com> containing several different sections.

## Learning

In this lab, you will be practicing with fetching data from a remote location. You will also be practicing many topics covered in the past two weeks.

Topics:

- Dynamic data display with template pages
- URL parameters
- The Document interface and its methods
- JavaScript Fetch API

## Achieving

In this lab, you will be creating a mock blog that fetches data from a remote location. You will need to dynamically render on template pages by utilizing information passed in the URL. 

Your work will result in:

- A landing page that displays a list of all authors and a list of all posts.
- When a user clicks on a linked author, it takes them to a page that lists all of the posts they authored.
- When a user clicks on a linked post, it takes them to a page that displays the content of that post.
- A dynamically rendered website that uses three HTML documents to display over a hundred pieces of data.

## Procedure

### Creating the file structure

- [ ] You will need the following HTML pages: `index.html`, `author.html`, and `post.html`
- [ ] You will need to create a `scripts` subdirectory that contains the following JavaScript files: `index.js`, `author.js`, and `post.js`.
- [ ] The `.js` files should be imported in their respective `.html` files.
- [ ] You will need to create a `styles` subdirectory. It is your choice if you use one `styles.css` for all three pages OR three css files that are respective to each page.

### Setting up your HTML pages

- [ ] On `index.html`, you will need elements to display the following information: a website title, a list of authors, and a list of all available posts.
- [ ] On `author.html`, you will need elements to display the following information: all posts by a specific author.
- [ ] On `post.html`, you will need elelemnts to display the following information: the post title, the post author, and the post content.

### Setting up your scripts

- [ ] On `index.js`, you will need to do the following:
- [ ] You will need to fetch users and posts from the placeholder data site.
- [ ] You will need to display the fetched data in the HTML elements on the page.
- [ ] When the user clicks on an author name, the link takes the user to the author page AND passes the author name to the new page in the URL.
- [ ] When the user clicks on a post, the link takes the user to the post page AND passes the post ID to the new page in the URL.
- [ ] On `author.js`, you will need to do the following: 
- [ ] You will need to grab the author parameter out of the URL and use it to fetch that specific author from the placeholder data site.
- [ ] You will also need to use the author parameter to fetch the specific posts by a specific author from the placeholder data site.
- [ ] Both the name of the author and the posts by that author should be displayed on the page.
- [ ] On `post.js`, you will need to do the following:
- [ ] You will need to grab the post id parameter out of the URL and use it to fetch that specific post from the placeholder data site. 
- [ ] You will also need to use the post id parameter AND use dot notation to access the author name of that post within the first fetch.
- [ ] The name of the author, the title of the post, and the content of the post should be displayed on the page.

## Review

In this lab, you built out a mock blog website that fetches data from a remote source and dynamically renders it on the page according to URL parameters.

The software should:

- Have a landing page that displays a list of all authors and a list of all posts.
- When a user clicks on a linked author, it takes them to a page that lists all of the posts they authored.
- When a user clicks on a linked post, it takes them to a page that displays the content of that post.
- Be a dynamically rendered website that uses three HTML documents to display over a hundred pieces of data.

## Going Further

- Create your own website design and realize it with CSS on all three pages.
- Incorporate a navigation bar so that users can return to the landing page from the author or post page.
