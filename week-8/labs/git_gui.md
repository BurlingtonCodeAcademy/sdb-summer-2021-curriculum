# LAB: GitHub GUI!

We've used Git commands in the terminal, but did you know that is different from using GitHub's user interface? In this lab we will be learning more about how what we do in the terminal with git commands translates to GitHub.

## These are your first steps...
---
We'll start as we always do when writing a new project that will be saved to GitHub, and make a repository or 'repo'. Do this by heading to [GitHub](https://github.com/) and signing in. Navigate to the repository tab and notice the collection of repo's you've created. Above these will be a green button labeled 'New' with a book emoji. Click this to get started on creating a new repository.

## Set up your repo
---
Every project begins with a brief, descriptive name. Enter one here, and be sure that it is different than any other repo name. For this lab, let's call it `bca-test-one`.

Next, set the privacy preferences. Would you like to make it available for anyone on the internet to see? If so, you can choose who is able to commit, or not. Otherwise you can make it private, and choose both who can see *and* commit to this repo. 

Lastly, let’s review what you can initialize your repo with.

### README.md file:
    Written in markdown, this file will automatically render on the main page of your repo and is used by visitors to learn a great deal about your project. It's up to you what to include, but a good README file generally lists:
    - a detailed project description. What does your program do, and why it is useful?
    - an instructional section that shares how users can get started, a list of dependencies, and info about the stack
    - links to documentation, a related forum, or a website
    - a changelog and planned updates, if any
    - a code of conduct and/or guidelines for contributors
    - a list of who maintains and contributes to the project 

 You can always add this later by adding a README.md file to the root level of your project. 

 ### .gitignore file: 
    This contains the names of files and directories that you want Git to ignore when making a commit. Often times these files include large packages and environment variables. When choosing to include a .gitignore file in this manner you’ll need to choose a template. More information on common .gitignore templates can be found here: https://github.com/github/gitignore. This file can also be added later.

### License:
    Let your contributors know what they can and cannot do with your code by writing a license. These are not common for projects like those created in the BCA bootcamp. More information about the types of licenses and what you may want to include can be found here: https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/licensing-a-repository

**For this lab, select a README file only**

Click that Create button and away we go!

## README much?
---
After you create your repo you will be taken to your new repository's main page. **Spend some time editing your README file.** This file will need to be written in Markdown language. Here is any [easy to use guide.](
https://www.markdownguide.org/cheat-sheet/) 

Include the following information:
 - Project Description: What is it your project, and why is it useful?
Technologies:
 - What technologies are used in your application? Include languages, libraries, and frameworks used, including version numbers.
 - Contributors: Who is working on your project? Connect relevant media such as github profile, twitter, or website links.

## Take a Tour
---
In this lab we will be exploring functionality of the main page. Notice the upper tabs however, including “Code”, “Issues”, “Pull Requests”, and more. **Take some time** to click through the tabs and read what each section has to offer. 

## Branching Out

Beneath the tabs are some repository controls. On the left is branch management, which appears as a button containing an emoji and the branch name `main`. Here you can create or switch between branches. If you remember, branches act as independent lines of development within your repository and are very powerful. 

When you initializing your repository, git creates a branch called `main`. This is your main codebase and should never be coded directly into. It is best practice to break a branch off of `main` and work in that. 

Go ahead and create a new branch by clicking the branch managment button. A dropdown menu will appear. Enter the new branch name `add_files`. Then click the prompt "Create branch: `add_files` from `main`".

You will be automatically switched into this new branch where we’ll write some code.

## File This Away

Next let’s make a file. Do this by clicking the "Add file" button to the far right of the branch management button. The drop-down menu that appears will allow you to create a new file or upload a file. Let’s create. 

Again we are taken to a new page. Enter the file name `test_one.txt`. This will create a text file that we can type plain text into. Note that github tells you which branch the file will be created in. Go ahead and write a few lines into this file.

At the bottom of the page are two options for saving (or committing) this file. Commit this one directly to the `add_files` branch. Be sure to add a commit message: “added a file for testing purposes” will do, or you can write your own.

Notice the alert that appears after being rerouted to the repository's main page: “add_files had recent pushes less than a minute ago”. Sure enough, our file exists just below our README.md. What do you notice about the other changes on the page?

You may have noticed that each file has a time signature next to it. The message above our file list has also changed. It should now read “create test_one.txt”. If you click the three dots next to that text, you’ll see your commit message appear as well as a number within a box. This is your commit id. It can be useful for large projects and workflow management, but we won’t cover that today.

To the right of the updated message you’ll see a timestamp of the latest repo activity and a clock with the number 2 next to it. This will take you to a page that lists all commit history changes, and offers further options to inspect, copy, and open the code at these commits. **Take a few minutes to poke around!** Try leaving a comment on your text_one.txt commit, and head back to the repo’s main page when you’re ready to move forward.

## Switching Branches

Switching between branches in this user interface is as easy as clicking a few buttons. If you are on your `add_files` branch, try clicking the branches button and head back to main. *Notice anything different?*

If you said "Hey! My file is missing.." then you’d be correct! You’ll notice that your timestamps and the commit clock reflects the changes on the branch you're currently on. **Head back to `add_files` and add some more files.** Notice that the text editor does not catch syntax errors or autofill like VSCode does?

## Push me Pull you

Now that you’ve added some files, let’s explore the "Compare and Pull Request" button inside the dashboard alert. A pull request gathers all changes made on the branch for you to examine before deciding what action to take, if any. You can see that under the heading ‘Open a pull request’ we have our base and compare branches. Here our base branch is `main`, and we are comparing it against `add_files`. There are no duplicate files or other outstanding issues, so we are given the message that yes, these branches are able to be merged. 

Scrolling down we see a pull request form and below that, information about the branch and it’s files, comments and contributors. You’ll also see that the files are expanded for review. Green highlighted lines are added lines of code; red are deleted lines of code. The bar next to each file name will also sum for you all additions and deletions for quick view.

By entering a comment such as “reviewed by ___ on MM/DD/YYYY. ” and clicking the ‘Create pull request’ button, you’ll be taken to a page that allows you to merge branches by merging your pull request or, writing a note and closing the request without merging. *You only want to merge your pull request if the branch has not conflicts with the base branch.* Go ahead and merge the branches. You’ll need to merge the pull request and then confirm the merge on the next page. Success!

## Nearly There

Go ahead back to the main page and take a look. Now the files from our `add_files` branch exist on the `main` branch. You can go back and access your old branches, but it’s best practice when moving forward after a merge to create a new branch to add further files and make changes to new ones. Create a new branch called `edits` and edit your test files. When you’re done (*and dont forget your commit messages!*) head to the `main` branch and click "Compare and Pull Request". Create your pull request and notice that the files you made changes in do not conflict with your base branch. Cool!

## On Second Thought...

This time, instead of merging, leave a comment like “needs further review” and close your pull request. Rather than merging your branches when the pull request is closed, the edits branch remains with unmerged commits. 

Head back to your edits branch and make more changes. When you’re ready, click the ‘Contribute’ button that is located to the right of the message ‘this branch is 2 commits head of main’. Open a new pull request and merge the branches. Heading back to the main repo page and our main branch, you’ll see that all files are updated. Ta da!

# Well Done!

Take some time to click around and explore the repo page. Come back to class ready with questions!

---
### Resources:
Markdown cheat sheet: 
https://www.markdownguide.org/cheat-sheet/
More info on pull requests: https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
