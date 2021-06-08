# Moving Around

When moving around on the terminal you use the `cd` command with the *relative path* to your desired destination.

`cd /code` would move you from my current directory into a subdirectory named `code`

`cd ..` Will move you from your current directory to the containing directory. `..` means "go up one level from my current location."

You can use more complicated relative paths to go through multiple directories

`cd ../../labs/bug-hunts` would take you up two levels (into the location that contains the directory that contains the directory you started in) then it will look for a sub directory named `labs` and a further subdirectory named `bug-hunts` which is where you end up when you hit <kbd>Enter</kbd>.

You can also hit <kbd>Tab</kbd> to autofill directory names after typing the first couple characters.

# Location, Location, Location!

In the terminal you are always *inside* a directory. When traveling through multiple directories it can be easy to get lost. There are a few helpful commands to show where you are.

If you're on MacOS you can use the command `pwd` to see where you are

If you're on a Windows machine your prompt in the command line will include the *full file path to your current location*. If you're using cmder you can also use the `pwd` command to print the full file path to your current location in the terminal.

# Creating Things

You can create files in the terminal by using the `touch` command and specifying the file name.

`touch index.js` would create a new file named `index.js` inside the current directory

You can also make subdirectories with the `mkdir` command

`mkdir labs` would create a new subdirectory named `labs` inside the current directory

# Running Programs

Many programs have a CLI (command line interface) that allows them to be run through the terminal. These commands are specific to the applications, and you can usually find instructions on how to use them in the program's documentation.

There are two programs we will commonly access through the CLI throughout this course, NodeJS, and VSCode

The command for NodeJS is `node`. Entering `node` by itself will change your terminal into a Node environment

Entering the command `node index.js` from the terminal (**NOT A NODE ENVIRONMENT**) will run the file `index.js` if it exists in the current location.

The terminal command for VSCode is `code`. To open VSCode from the directory you're currently in you can use the command `code .`
