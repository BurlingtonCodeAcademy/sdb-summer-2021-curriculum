# Hello Friend, Go Away Enemy

# Objective

## Learning

In this lab, we will be practicing with Boolean operators and conditional statements. We will also play with function parameters and arguments. 

Topics:

- Boolean operators ( `||` the logical OR).
- `if...else` Conditional statements.
- Functions; their parameters and arguments.

## Achieving

In this lab, we will be achieving a piece of software that determines if a name belongs to a friend or enemy dependent upon the argument passed to its function.

Your work will result in:

- A file called `helloFrenemy.js`.
- Within `helloFrenemy.js`, a function named `greeter` to handle our greeting logic.
- Within `greeter`, a series of `if...else` statements that determine if the argument passed into the function is a name that belongs to a friend or an enemy.

# Procedure

## Creating  the `helloFrenemy.js` file

- [ ] Navigate to your `code` folder in the command line.
- [ ] Use the command `mkdir` to create a new subfolder named `hello-frenemy`.
- [ ] `cd` into `hello-frenemy`.
- [ ] Use the command `touch` to create a new file named `helloFrenemy.js`
- [ ] Open `helloFrenemy.js` in your editor.

## Creating the `greeter` function

- [ ] Within `helloFrenemy.js`, declare a function named `greeter`.
- [ ] `greeter`'s function call should accept the parameter `name`.
- [ ] Within `greeter`'s code block, create an `if` statement whose conditional statement checks if `name`'s value is that of an enemy.
- [ ] Within this `if` statement's code block, add a console log telling your enemy to "Go away!"
- [ ] At the end of the `if` block, add an `else` whose code block contains a console log. This console log should concatenate "Hello, " and `name` into a friendly greeting.

## Calling the `greeter` function

- [ ] Below `greeter`'s code block, make multiple calls of `greeter` to test if your function recognizes the name of an enemy versus the name of anyone else.
- [ ] With the `node` command, run `helloFrenemy.js`  in your terminal to see the result.


# Review

In this lab, we have built a piece of software that determines whether or not someone is our enemy or a friend. The software should:

- Print one of two responses to the terminal; these responses should be dependent on the argument passed to the function when it is called.

## Going Further

- Have the names be greeted in the same format regardless of how they are passed to the function. Even if the function receives "fRiEnD", it should print "Friend".
- Sanitize the input so that enemies cannot sneak in with odd capitalization, such as "eNEmY".
- Handle full names so the printed response is "Hello, First Last!"
