# Welcome!

Welcome to your software development program!

This invaluable skill will challenge and develop you into a creative problem solver if you put in the work.

Let's get started!

---

# What is code?

**Code** is saying one thing to mean something else. In computer science, it refers to how we write out instructions.

**Code** is a _tool_ used to give the computer _instructions_ to later follow.

These instructions are called **programs**.

**Coding is writing.**

---

# Programmatic Thinking

- It's easy to immediately start writing code. Don't. Figure out the instructions needed first.
- Imagination and scratch paper go a long way when planning.
- Computers follow programs exactly as written.
- Computers _sometimes_ show error messages to help the programmer.
- Always **test** _before_ submitting.
- Mistakes are expected and respected. Try again.

---

# Programming Languages

- Every program is written in a **language**:
  - Anyone can make a computer language
  - Different languages are good at different things
  - The manual is called **documentation**. Read it.
- Computer languages are not ambiguous. Specific words mean specific things.
- We will be learning JavaScript, HTML, and CSS -- the languages designed to build the web.

---


# The Terminal

- We use the **Terminal** application to tell the computer commands.
  - The terminal gives us a **command line** that is managed by a **shell**.
  - The **console** in your browser is a kind of terminal. 
  - *command line*, *console*, *shell*, and *terminal* are often used interchangeably. 
- Some apps only exist in the terminal and are seemingly invisible.
  - These are _CLI_ (Command Line Interface) applications.
- Some display a window for the user to interact with.
  - These are _GUI_ (Graphical User Interface) applications.
- Developers use the _terminal_ for its ease-of-access, speed, and power.

---

# Directories

- **Directories** are folders on your computer
- Directories can contain
  - files
  - directories
- We can use the command line to navigate and manipulate directories and their contents.

---

# Navigation

- The terminal is always referencing some directory, as if it were inside that folder.
- This helps it make sense of commands.
- It makes navigating your computer feel more like exploring rooms in a house.
- It's common to need to ask, "Where am I?"
- We can tell the computer to `print` or `log` things we want to see.
- We can use the terminal to say, "_Print_ the _working directory_," by typing <kbd>p</kbd><kbd>w</kbd><kbd>d</kbd> and hitting <kbd>Return</kbd>
- The terminal might also list the current directory whenever it's ready for commands.

---

# The Path

The command line is very dependant on the file **path**. Here are a few key directional commands in the command line:

- `.` means "this directory I'm currently inside of"
- `..` means "the directory containing the directory I'm currently inside of"
- `/another-directory` means "look for a directory named `another-directory` inside of the current directory
  - Paths can also be chained to go through multiple subdirectories
  - e.g. `/another-directory/further-down`
  - When `cd`ing into subdirectories hitting <kbd>Tab</kbd> will autofill the directory name after typing at least one character

---

# Basic Commands

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

# Opening Programs

When you "open" an app, you usually click an icon. But what about CLI programs?

To run a program in the terminal, use a preset key word followed by the file or directory name.

Example:

- To open VSCode from the command line you can issue the command `code .`
  - `code` is the keyword to open VSCode
  - `.` means "from this directory I'm currently in"

---

# JavaScript in the Terminal

When we installed Node, we gave ourselves the ability to use JavaScript in the terminal.

This lets us run JavaScript files and test out ideas quickly.

- To use JavaScript, we need to run Node.
- You can check that Node is installed with the command `node --version`
  - If Node **is NOT** installed, this error is shown: `node is not recognized as an internal or external command`
  - Typing `node` by itself and hitting <kbd>Return</kbd> will start Node inside your terminal
  - To exit, hit <kbd>CTRL-C</kbd> twice
