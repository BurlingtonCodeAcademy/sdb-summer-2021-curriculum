# Intro to Git Branches

As we learned in week one, *git* is a distributed version control tool used for tracking changes to files.

It acts like an easily updatable file system that stores a log of changes to the codebase including:
 - Who made each change
 - Why they made it
 - And when they made it

---

But let’s say you’re working concurrently on a project with several developers. How do we manage what happens when those different code bases are pushed up to GitHub? And how do we get the new code written by each person?

Enter, 

    ~git branches~ 

---

# What is a branch?

A “branch” is split off of the main codebase. This main codebase is in itself your default branch, called `main`. It is an independent line of development, a pointer to a moment in your code’s history. A branch allows you to make changes to the codebase, acting as a container for code that solves a certain bug or relates to a certain feature, isolated from the codebase on GitHub.

---

# But why branches?

A branch always points to a commit, which allows us to:
 - roll back the codebase to a specific feature if needed
 - Review code before it is merged in to the main branch
 - Compare different files to view specific changes, when they were made, and by whom

As well as manage merges so that a team can work together efficiently

---

# Making a branch

 - To create a branch, enter the command `git checkout branch_name`
 - Git will automatically transfer you to this new branch
 - The branch name should describe the feature you are building or the bug that you are solving

---
# Saving a branch

Once work on a branch is complete, changes must be added, committed, and pushed to the remote repository before being merged into the main branch. Same as we usually do.

```javascript
git add . 	// this gathers all changes and stages them
git commit -m “commit message”  	// these are crucial to your collaborators and future you!!
git push	// send the changes off to your repository
```

---
# Branching Strategies

Different teams will choose different strategies for managing their branches. These strategies are also called “workflows”. Some common workflow styles include:

The Centralized Workflow
Feature branching
Forking Workflow

--- 
# Feature Branching

We use Featuring Branching because it allows for a *continuous integration environment* amongst multiple developers. 

The bottom line: All feature development should happen in a dedicated branch for that feature, and be merged into the main branch when completed.

---

# Feature Branching Basics

Branches are short lived and focus on **one** feature at a time. 
They should be branched off the updated main branch and be merged quickly. 
This will require **frequent and effective communication** with your team!

---

# Merging branches

`git merge` takes a branch and connects it to another.
Usually you merge *to and from* `main` into a *feature branch*

To *merge* is to create a *new commit* on the current branch
That “merge commit” has two parents and represents all changes from both branches

---
# Merge Commands

Before merging, ensure your feature branch is fully saved by giving the command `git status`.  

Next, head to the branch you want to merge your feature branch into. In our workflow, it would be the main branch. Give the command `git checkout main`. 

Give another `git status` command to ensure the main branch is up to date with your repository. If it is not, pull down the changes by giving the command `git pull`.

Next, we merge! Give the command `git merge feature_branch_name` to bring the branches together.

---

# LAB: Git GUI

Let’s dive in to a more comprehensive, hands-on lesson of git branches using the GitHub user interface. This will help us visualize how branches work and get practice with the many git commands and work flow.

---

# LAB: Git GUI

---
# Reflection

Temperature check on git commands and branches
What are some observations that you made?
What were some of the challenges you faced?

---
# Git CLI
Now get some practice using these same commands in the CLI. This will be a more streamlined approach to the system we just used in the GitHub user interface. 
---

# LAB: Git CLI

---

