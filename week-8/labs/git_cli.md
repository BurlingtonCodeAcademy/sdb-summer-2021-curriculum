# LAB: Git from the CLI
---

Now that we’ve played with the github GUI, let’s work from the command line.

## On your marks...

While it's true that GitHub and Git are not connected, we *can* and *want* to connect them. That way when we write on our local machine, we have somewhere in the cloud to send and save our codebase. Begin by heading to your profile at [GitHub.com.](https://github.com/). Make a new repository there called `bca-test-two`. Don't worry about adding anything to the repo yet. The next page you see should read "Quick setup -- ". Perfect. Let's pause here and open a new terminal window on our machine.

## Get set....

`cd` into your code directory and create a new sub-directory called `bca-test-two`. *Be sure to `cd` into this new sub-directory before moving forward!* Once inside run the command `git init`. Notice the message we recieve: "`Initialized empty Git repository in...`". Excellent!

## GO!

We're all ready to connect our GitHub repo and the repo we just created on our machine. It's as easy as 1-2-3! Enter the command `git remote add origin git@github.com:*[your_username]*/bca_test_two.git`. It won't look like much has happened.. and that is part of the magic!

## Housekeeping

Before we hop into coding let's get our main codebase saved to GitHub with a clean slate. Give the following commands:
    * `touch README.md` to create our README file. 
    * `git add .` gathers all of the changed files and stages them to be saved
    * `git commit -m "[your commit message here]"` creates a commit message
    * `git push -u origin master` completes the save

Head back to your main repository page on GitHub to see that you've successfully connected your repositories; there should be a commit message and a README.md file that wasn't there before!

## Make a branch

In the terminal, give the command `git checkout -b add_files`. The characters after `-b` make up your branch name, so be descriptive! Giving this command will result in the message "Switched to a nwe branch 'add_files' and next to your filepath, the branch name will appear in parenthesis. Very helpful!

## Add a file

Add a file without even opening VS Code by giving the command `touch test_one.txt`. Now give the command `code .` to open VS Code and enter some characters into this plain text file. When you're ready, head to the top of VS Code and create a new terminal from the Terminal dropdown menu. What do you notice?

## Same old same old

Maybe you noticed the following:

 - a new terminal will appear on the bottom of your VS Code window. 
 - like your computer's terminal, a filepath will appear. It lacks the parenthesis that denotes the branch name however. So how can we check?

In the very lower left hand corner of the window is a small emoji that should look familiar; it's our branch emoji friend from the last lab! Beside it is the branch name that you are currently on. Sure enough, if you give the command `git checkout add_files` you will receive the message "Already on `add_files`. Looks like this terminal is the same as our machine's. Cool!

## Practice makes perfect

Save your changes by entering the commands from the Housekeeping story, with one change. You will have to enter `git push -u origin add_files` the first time saving to this new branch. Notice the message that is returned? This details the push progress, total number of files, and more information.

## Switcheroo

Let's head back to the `master` branch by giving the command `git checkout master`. Keep your eyes on your files. Much like in the GUI lab, files present in your `add_files` branch are not present on your `master` branch and vice versa. Two bring the files from `add_files` over to `master`, we'll preform a merge. Let's try that next!

## Merging Lanes

Unlike the GUI where we created a pull request from which we merged branches, the way to merge from the terminal is to give the simple command `git merge add_files`. Ta da! Much simpler. If you check the repository on GitHub however you won't be able to see this change. Why? Enter the command `git status` in your terminal to see why.

## It takes Commitment

You should have received the message "Your branch is ahead of 'origin/master' by 1 commit.' Meaning, our local codebase and our cloud codebase are not up to date. To save your merge and resolve this run the commands as we have before:
    * `git add .`
    * `git commit -m "merged add_files to master branch"`
    * `git push`
    
You only need to enter `git push` and not the longer `git push -u origin/master` because that is used the first time a push is made from a local branch to create a connection with the remote one on GitHub. Afterwards, `git push` works just fine.

Enter `git status` to check that your local branch is up to date with 'origin/master'. Well done!

## Practice practice practice

Make some more branches and add files to them. Switch between branches and practice merging them. Building muscle memory will serve you down the road!