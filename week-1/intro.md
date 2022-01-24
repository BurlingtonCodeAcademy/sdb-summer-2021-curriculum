# Welcome!

Welcome to your software development program!

This invaluable skill will challenge and develop you into a creative problem solver if you put in the work.

Let's get started!

---

# What is code?

**Code** is saying one thing to mean something else. In computer science, it refers to how we write out instructions.

**Code** is a _tool_ used to give the computer _instructions_ to later follow.

These are instructions are called **programs**.

**Coding is writing.**

---

# Programmatic Thinking

- It's easy to immediately start writing code. Don't. Figure out the instructions needed first.
- Imagination and scratch paper go a long way when planning.
- Computers follow **programs** exactly as written.
- Computers _sometimes_ show **error** messages to help the programmer.
- Always **test** _before_ submitting.
- Mistakes are expected and respected. Try again.

---

# Programming Languages

- Every program is written in a **language**:
  - anyone can make a computer language
  - different languages are good at different things
  - the manual is called **documentation**. Read it.
- Computer languages are not ambiguous. Specific words mean specific things.
- We will be learning JavaScript, HTML, and CSS -- the languages designed to build the web.

---

# What will we learn?

Throughout this course, you will learn about:

- Common programmer tools.
- Common parts of programming languages used to write programs.
- Thinking like programmers.
- How to make simple websites.
- How to make Single Page Applications, i.e. more complex websites.

---

# Technical Requirements

See the [Installfest](/week-1/articles/installfest) project for more instructions.

Software

- a text editor - VSCode <https://code.visualstudio.com>
- JavaScript - Node.js <https://nodejs.org>
- version control software - git version 2.x <https://git-scm.com>
- open-source sharing site account - GitHub <https://github.com>

---

# Technical Requirements cont.

- Heroku
  - **Sign up** for an account at <https://signup.heroku.com>
  - **Install** the _Heroku Command Line Interface_ (CLI) at <https://devcenter.heroku.com/articles/heroku-cli>
- Postman
- MongoDB and Compass

- Please stop right now and check
- If you do not have these, let us know!

---

# Introducing: The Command Line!

- We use the **Command Line** application to tell the computer _commands_.
  - AKA _console_ or _terminal_ or _command prompt_ or _shell_
- Some apps only exist in the terminal and are seemingly invisible.
  - These are _CLI_ (Command Line Interface) applications.
- Some display a window for the user to interact with.
  - These _GUI_ (Graphical User Interface) applications.
- Developers use the _terminal_ for its ease-of-access, speed, and power.

---

# Directories

- _Directories_ AKA _folders_ organize items into groups
- directories can contain
  - _files_
  - other _directories_
- We can use _the command line_ to navigate and manipulate _directories_ and their contents.

---

# Where am I?

- The terminal is always referencing some directory, as if it were inside that folder.
- This helps it make sense of commands.
- It makes navigating your computer feel more like exploring rooms in a house.
- It's common to need to ask, "Where am I?"
- We can tell the computer to `print` or `log` things we want to see.
- We can use the terminal to say, "_Print_ the _working directory_," by typing <kbd>p</kbd><kbd>w</kbd><kbd>d</kbd> and hitting <kbd>Return</kbd>
- The terminal might also list the current directory whenever it's ready for commands.

---

# The Path

The command line is very dependant on the file path. Here are a few key directional commands in the command line:

- `.` means "this directory I'm currently inside of"
- `..` means "the directory containing the directory I'm currently inside of"
- `/another-directory` means "look for a directory named `another-directory` inside of the current directory
  - Paths can also be chained to go through multiple subdirectories
  - e.g. `/another-directory/further-down`
  - when `cd`ing into subdirectories hitting <kbd>Tab</kbd> will autofill the directory name after typing at least one character

---

# Basic Commands (Unix)

- "Print Working Directory"
  - command: `pwd`
  - use case: shows the name of the current directory
- "List"
  - command: `ls`
  - use case: shows the contents of the current directory
- "Make Directory"
  - command: `mkdir`
  - use case: creates a new directory inside the current one
- "Change Directory"
  - command: `cd`
  - use case: move into a different directory

> These apply to Mac / Unix / Linux / bash

---

# Basic Commands (DOS)

- `cd` ("change dir") -- With no directory, it lists the current directory. Otherwise, it changes to the specified directory
- `dir` ("directory") -- shows the contents of the current directory
- `mkdir` ("make dir") -- creates a new subdirectory inside the current directory

> These apply to Windows / DOS / PowerShell

---

# Running Programs

To run a program in the terminal, use a preset key word followed by the file or directory name.

Example:

- To open VSCode from the command line you can issue the command `code .`
  - `code` is the keyword to open VSCode
  - `.` means "from this directory I'm currently in"

---

# JS in the CLI

When we installed Node, we gave ourselves the ability to use JavaScript in the terminal.

This lets us run JavaScript files and test out ideas quickly.

- To use JavaScript, we need to run Node.
- You can check that Node is installed with the command `node --version`
  - If Node **is NOT** installed, this error is shown: `node is not recognized as an internal or external command`
  - Typing `node` by itself and hitting <kbd>Return</kbd> will start Node inside your terminal
  - to exit, hit <kbd>CTRL-C</kbd> twice
