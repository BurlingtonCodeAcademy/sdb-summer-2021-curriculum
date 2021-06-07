# Welcome to the Burlington Code Academy!

---

# What is code?

In general, code is something that stands for something else.

In computers, code is a series of instructions that tell a computer what to do.

---

# What is coding?

* coding (aka programming or software development) is a *creative, human* activity
* *coding* does not mean "cracking the code" or "deciphering" -- it's not a mystery or a secret, at least no more than any other language
* the words (and numerals and punctuation) we write are translated into long strings of ones and zeros
* the computer interprets the code, and takes the actions it describes

---

# Programmatic Thinking

Throughout this course one of the most important skills you will learn is how to think like a programmer.

Computers are weird, and very literal. Here are a few things to keep in mind when working with them:

* Computers are very fast, but not very smart. They will only ever do exactly what you tell them to
* Computers are really bad at being random. There's always a pattern, though it's not always obvious
  * When you run into a bug, try and replicate it. If you know the actions that break your code it's easier to guard against them
* Getting a different error is good. It means you're making progress so don't get discouraged!
* Build things for fun, and to learn!

---

# Languages

* Every program is written in a LANGUAGE
  * like Java or Python or C or Fortran or Lisp or...
  * even HTML and CSS and SQL are languages
  * every computer language has a silly name
* Computer languages are very **specific** compared to natural languages
* Different languages are useful in different areas, but there is a lot of overlap
* Over the next several months we will be learning JavaScript, HTML, and CSS

---

# What will we learn?

In this class, you will learn about:

* The command line and why we use it
* Strings, Arrays, Variables, Objects, Loops, Files
* How to run your code interactively or from a file
* How to make a very simple website run on your own computer
* How to make a not so simple application run on the web

Follow along online! Put a browser pointed at this site on one side of your screen, and Terminal on the other.

---

# What if I know some of this already?

* Pair up
* Help your partner, help your neighbor
* Promote yourself to TA

---

# Errors Are Awesome

* Don't be afraid of errors
* Your computer is trying to help you fix your program
  * It's just *really* bad at communicating

> If your code is a two-year-old child, then an error is a temper tantrum.

(It can take effort to figure out the underlying reason why they're upset and fix it.)

* It's not all gibberish
* Try to read it -- really try! -- and pull out the pearls from the pig slop

See also: [What went wrong?](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_went_wrong) from MDN

---

![Breakdown of error message](https://res.cloudinary.com/btvca/image/upload/v1622657526/curriculum/error-message-breakdown_jpmlv0.png)

---

# Technical Requirements

See the [Installfest](/projects/installfest) project for more instructions.

Software

- a text editor - VS Code from Microsoft <https://code.visualstudio.com>
- JavaScript - a live node.js installation
- Git - version 2.x
- GitHub 
  - **Sign up** for an account at <https://github.com/>

---

# Technical Requirements cont.

- Heroku
  - **Sign up** for an account at <https://signup.heroku.com>
  - **Install** the Heroku Command Line Interface (CLI) at <https://devcenter.heroku.com/articles/heroku-cli>
- Postman
- MongoDB, and Compass

- Please stop right now and check
  - If you do not have these, let us know!

---

# Introducing: The Command Line!

* the **Command Line** is a window into which you can talk directly to your computer
  * aka *console* or *terminal* or *command prompt* or *shell*
* when you type into the terminal, you are issuing **commands** to the computer
* a *CLI* (Command Line Interface) is different from the *GUI* (Graphical User Interface) you are used to
  * a CLI is more primitive **and more powerful** than a GUI

---

# Directories

* a *directory* is a location on your hard disk
  * also called a *folder*
* directories can contain *files*
* directories can also contain other directories (called *subdirectories*)

---

# Where am I?

* Inside the Terminal, you are always "inside" a directory.
* It is very easy to get lost in a maze of directories.
* To find out which directory you are in, type <kbd>p</kbd><kbd>w</kbd><kbd>d</kbd> and then hit <kbd>Return</kbd>
  * This stands for "print working directory" (not "password").
  * Most of the time you can also look at the prompt to see what the current directory is.

---

# The Path

The command line is very dependant on the file path. Here are a few key directional commands in the command line:

* `.` means "this directory I'm currently inside of"
* `..` means "the directory containing the directory I'm currently inside of"
* `/another-directory` means "look for a directory named `another-directory` inside of the current directory
  * Paths can also be chained to go through multiple subdirectories
  * e.g. `/another-directory/further-down`
  * when `cd`ing into subdirectories hitting <kbd>Tab</kbd> will autofill the directory name after typing at least one character

---

# Basic Commands (Unix)

* `pwd` ("print working dir") -- shows the name of the current directory
* `ls` ("list") -- shows the contents of the current directory
* `mkdir` ("make dir") -- creates a new subdirectory inside the current directory
* `cd` ("change dir") -- move into a different directory

> These apply to Mac / Unix / Linux / bash

---

# Basic Commands (DOS)

* `cd` ("change dir") -- With no directory, it lists the current directory. Otherwise, it changes to the specified directory
* `dir` ("directory") -- shows the contents of the current directory
* `mkdir` ("make dir") -- creates a new subdirectory inside the current directory

> These apply to Windows / DOS / PowerShell

---

# Running Programs

You can also run programs through the command line. To run a program through the command line, you type a preset keyword for the type of program you want to run, and then the name of the file you want to run.

* To open VSCode from the command line you can issue the command `code .`
  * `code` is the keyword to open VSCode
  * `.` means "from this directory I'm currently in"
  * You should always `cd` into the directory you want to be working in, then open VSCode from the command line
  * Don't open VSCode through the GUI!

---

# JS in the CLI

You can also write JavaScript directly in th command line. This is a great way for testing out code snippets, and operations!

* To write JavaScript you need to be in a "Node" environment
* You can check that Node is installed with the command `node --version`
  * If Node **isn't** installed you'll get the error: `node is not recognized as an internal or external command`
  * typing `node` by itself and hitting <kbd>Enter</kbd> will open a Node environment inside your terminal
  * to exit a Node environment hit <kbd>Ctrl</kbd> and <kbd>C</kbd> twice
