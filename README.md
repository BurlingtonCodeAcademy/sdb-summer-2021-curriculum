# Software Development Bootcamp -  June 2021 Curriculum

## Welcome

This repository holds slides, exercises, and labs for the  software development bootcamp, for June of 2021.

You are able to view the curriculum in the form of [Markdown](https://commonmark.org/) files, and these files are converted into HTML using various processing tools.

The primary tools that we use for this conversion is Babel, Webpack, Spectacle, and React-JSX.

You can view the output of the **slide** conversion while authoring by following the steps below in `Getting Started`.

> Additional authoring tools will be added soon which will allow for the exercise and written content to be viewed as well.

## Getting Started

1. Install Spectacle-CLI

    ```sh
    $ npm install -g spectacle-cli
    ```

1. Start the webpack server. The server will run at address: [`localhost:3000`](http://localhost:8080).

    ```sh
    # from the project root directory

    $ spectacle-cli -s <CURRICULUM-WEEK>/<LESSON>.md -t src/theme.js
    ```

    ```sh
    # example below for a real lesson

    $ spectacle-cli -s week-1/variables.md -t src/theme.js
    ```

> More Information about using the Spectacle-CLI to run your presentation:
> https://formidable.com/open-source/spectacle/docs/basic-concepts/#mdxmarkdown

## Spectacle Links

- [Reference](#reference)
- [Getting Started](#getting-started)
- [Tutorial](#tutorial)
- [Build & Deployment](#build-deployment)

### Reference

The Spectacle core API is available in the [Spectacle Docs](https://github.com/FormidableLabs/spectacle/blob/main/README.md).

## Spectacle Tutorial

If want you a step-by-step guide for getting started with Spectacle, a basic tutorial is available [here](https://github.com/FormidableLabs/spectacle/blob/main/docs/tutorial.md).
