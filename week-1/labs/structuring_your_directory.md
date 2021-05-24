# Using the Command Line

## Welcome!

The purpose of this lab is to help you get  little more comfortable interacting with your computer through the command line. The command line (a.k.a. shell, terminal, etc.) will be our primary way of interacting with our programs throughout this course so it's important we get comfortable using it.

In this lab you will set up the basic directory structure you will use to keep your code organized throughout this class, and you will write, and run a JavaScript program on your local machine.

Go ahead and open your terminal now. On a Mac it will be an application called "terminal." On a PC, if you followed the installfest instructions, you should have an application called "cmder" as your terminal. If you are having any issues with the terminal let your teacher know, I can help! 

## Where Am I?

When you open your terminal it is always opened from *inside* a directory. By default this will usually be your home directory: `C:\Users\yourUserName`. You can always check where you are currently located in your computer with some console commands:

- `cd` all by itself on a Mac will print your current location
- `pwd` on a a PC will do the same thing. On a PC your prompt is also your current location

We can see all directories, and files in our current location by typing in `ls`

Try this now.

In your home directory you should have quite a few other directories. "Directory" is just a fancy word for "folder."

## Moving Between Folders

One of the directories that lives inside your home directory should be called "Documents." Let's move ourselves into that directory.

You can change directories with the command `cd` followed by the name of the directory you want to enter. To move int "Documents" we would type `cd Documents` You can also hit the <kbd>Tab</kbd> key to autocomplete directory names after you type a few characters.

To move to the containing directory with the command `cd ..` the `..` tells the terminal to go up one level from its current location.

Typing `cd ..` from inside "Documents" should take us back to our home directory

You can also go directly to the home directory from any location by typing `cd ~` on a Mac or Linux computer, or `cd %HOME%` on a PC.

## Creating New Folders

Let's go back to our home directory (if you aren't already there) and set up a new directory for the code we'll write during this course. You can use the `mkdir` command followed by the name of the directory you want to create.

Let's use the command `mkdir code` to make a new directory named "code"

Note that creating a new directory **does not** move you into it, it just creates it.

## Creating a File

Use your terminal to go into your newly created "code" directory. Double check to make sure you're inside the "code" directory!

You can create new files by using the `touch` command followed by the name of the file you want to create.

Make sure you're in the "code" directory, then create a file called `hello.js` using the command `touch hello.js`

## Opening VSCode

When we're working with programs in the command line it's very important to make sure we are opening things from the proper directory, and we are running files from the correct location otherwise we will get errors because the computer can't find the file you're trying to run in the location you told it to run from.

To make your life easier you should **always** open VSCode from the terminal. You can do so by issuing the command `code .`

  - `code` is the command to open VSCode
  - `.` means "from this location I'm currently in

If you run into any issues with the `code` command reach out to your instructor, or one of the TAs, it's what we're here for!

When you open VSCode from inside your "code" directory you should see a single empty JavaScript file named "hello.js"

## Your First Program

Click on the file "hello.js" in the file explorer on the left-hand side of VSCode, and add the following line of code to it:

```js
console.log("Hello, world!")
```

## Running a File

Since "hello.js" is a JavaScript file we want to run it in a NodeJS environment. We can do so by using the command `node hello.js` in the terminal. Please note that this will only work if you are **inside** your "code" directory, where that file lives. Otherwise your computer won't be able to find the file!

When it runs successfully your program should print "Hello, world!" to the console.

You can also use the `node` command without a file to enter a node environment in your terminal. This will allow you to write JavaScript directly in your terminal, and is a great way to try out some of the simple code snippets you might come across in our slide decks.

Congratulations! You're a programmer now!
