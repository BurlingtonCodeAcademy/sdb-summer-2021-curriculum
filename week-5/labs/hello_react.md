# Hello React!

## Welcome!

Let's create our first React application. This will be a fairly trivial React app as the main purpose for this lab is to get you used to give you experience setting up React applications from scratch, and to give you a better understanding of React's required packages, and how they work together.

## Creating the Repo

React is dependant on several packages working together. To bring thess packages in we will need to install them from npm. To bring in packages we firs need to create a new repo to work in.

`cd` into the repo and run the command `npm init -y`. This will get the repo ready for installing packages by creating a `package.json` file that will track our dependencies.

## Installing Dependencies

The first dependency we will need to install is called "babel". Babel is a compiler that allows us to extend JavaScript and write JSX code. We need three parts of the Babel framework for React in a development environment, and since we only need them in a dev environment we can save them as dev-dependencies so that there's no chance of them interfering with our production code. We can import all those parts at once with the command-line command:

`npm install --save-dev @babel/core @babel/preset-env @babel/preset-react`

To prepare our directory for React we will also need a *static module bundler* that will allow us to more easily import multiple JS files into our site, as well as allow us to load other file types in. We will be using the Webpack application for this, and again we only need it as a dev dependency. We also need 3 aspects of Webpack and we can install all of those with the command:

`npm install --save-dev webpack webpack-cli webpack-dev-server `

We will also need *another* framework to make Webpack and Babel play nicely which we can install with:

`npm install --save-dev babel-loader`

Once we have all these dependencies installed that will help our browser deal with the React code we can install the main React packages:

`npm install react react-dom`

Note that these **are not** dev dependencies.

## Hello File Structure

Once everything is set up and installed you should have 2 new files, and a new sub directory.

The files are `package.json` and `package-lock.json` which track your dependencies, and your dependencies' dependencies respectively. You will never need to and *should never* modify your `package-lock.json` file. The subdirectory should be named `node_modules` and this is where all the packages you just installed live. Like `package-lock` you should never need to dig into your `node_modules` folder.

Let's create 2 new subdirectories named `src` and `public`. We will be creating our React components in the `src` folder, and rendering the contents of `public` in the browser

Inside `src` create a file named `app.js`. This will serve as our root level React component.

In `public` create a file named `index.html`

## Setting up `webpack` and `babel`

Now we need to tell webpack and babel how to bundle, and serve our React code. To do this we'll need to set up a couple of configuration files at the root level of our project directory.

For webpack this file will be named `webpack.config.js` and contain the following code:

```js
const path = require('path')

module.exports = {
  entry: './src/app.js',
  output: {
    filename: 'bundle.js',
    path: path.join(__dirname, 'public')
  },

  module: {
    rules: [{
      loader: 'babel-loader',
      test: /\.js$/,
      exclude: /node_modules/
    }]
  },

  devServer: {
    contentBase: path.join(__dirname, 'public')
  }
}
```

This tells webpack that when it gets a "build" command it should grab all the code from our `app.js` file, and use it to generate a file named `bundle.js` which will contain the computer compiled, plain JS version of your react code, and put it into the `public` folder. It also tells webpack to use the Babel rule set for all JS files, except those coming from our `node_modules`. In addition it set's up a development server to server the files from the `public` folder.

We also need to set up a `babel.config.json` file (again in the root level of our project directory) to tell babel which rule sets it should use for the `babel-loader`. The contents of this file should look like this:

```json
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ]
}
```

## Getting `index.html` Ready

To make sure our React components show up on our page we also need to do a little setup in our `index.html` file. Open this file, and create your standard HTML shell, then add two elements in the `body`:

`<div id="root"></div>`
`<script src="bundle.js"></script>`

That's all you need to do in the `index.html`.

## Adding Scripts

To build our front end code, run our server, and be able to see our site easily we should add a few scripts to our `package.json` file.

To add scripts open up `package.json` and look for the `scripts` section. Currently there should be a single `test` script. Modify your `scripts` section so it looks like this:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "build": "webpack",
  "start":  "webpack serve"
}
```

To view your site you run the command `npm run build` to bundle the code, and send it to our `public` directory, and then `npm run start` to start the server so you can view your site. By default it should serve your site on "localhost:8080".

## Hello Components

When you view your site at this point you see a blank page because we haven't created any content yet, so let's create our first component!

In your `app.js` import the React framework with the following import method:

```js
import React from 'react'
```

In that same file create a new class based component named `App`, and have it render an `h1` that says "Hello, React!"

To tell React to put this on the page we will need to use a `ReactDOM` method so we will need to import `react-dom` as well:

```js
import ReactDOM from 'react-dom'
```

Then we can put the component we just created on our page by using the `ReactDOM.render` method, passing the component we want to put on the page as the first argument, and the location on the page as the second argument.

```js
ReactDOM.render(<App />, document.getElementById('root'))
```

## Building and Viewing

Run the build command again, and restart your server to see the new content you just created appear on the page.

## `create-react-app`

It's a bit of a pain to go through the whole setup process every time you want to create a React site, but we don't have to!

There are packages you can install that will allow you to use CLI commands to generate the entire React setup automatically, set up all the config files, link everything together, and set up all the necessary scripts.

`create-react-app` is one of these tools that is very widely used. To generate a new React project with `create-react-app` you will first need to install it in the directory you want to create your React app in. Once you've installed it you can run the command `npx create-react-app project-name` to generate a new repo (in this case called `project-name`) which will hold the entire React setup, ready to go.  You can start the app by `cd`ing into the directory that was just created and running the command `npm start`

The `npm start` command in a project generated with `create-react-app` will start up a *development server* that will hot reload as you change components, so you can see your changes being rendered in real time without having to run a build step or restarting the server.

## Warning! Git Repos in Git Repos

When `create-react-app` generates a new directory it also initializes it as a git repo. This can cause issues if your containing directory is *also* a git repo, as git tends to throw a fit when you put repos inside other repos.

To *de-initialize* a git repo you can run the command `rm -rf .git` from inside that repository. It's generally not a bad idea to do this in any directory generated with `create-react-app`.
