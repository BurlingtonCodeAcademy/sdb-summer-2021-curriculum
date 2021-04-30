# Git

*git* is a distributed version control tool

used for tracking changes to files

---

# What is a Version Control System?

It's like a filesystem, plus:

  * a log of changes to the files
  * including *who* made each change
  * and *why* they made it

---
  
# Why is Version Control Important?

* For a dev team?
* For an individual on that dev team?
* For a product manager or client?
* For a sysadmin?
* For a QA (Quality Assurance) engineer?

---

# Installing Git

* Instructions vary based on your operating system
* MacOS with Homebrew: `brew install git`
* MacOS without Homebrew: https://git-scm.com/download/mac
* Windows: https://git-scm.com/downloads/win
* Linux: https://git-scm.com/download/linux

---

# Git vs GitHub

[git](https://git-scm.com/book/) is a *distributed version control tool* that was built by Linus Torvalds in 2005 to help him manage the Linux Kernel project

[GitHub](https://github.com/) is a *centralized collaboration website* that was [started in 2007](https://www.inc.com/30under30/christine-lagorio/github-pj-hyett-chris-wanstrath-2013.html) by Tom Preston-Werner, Chris Wanstrath and P.J. Hyett, and was acquired by Microsoft in 2018

> Does Linus use GitHub? Not much: <https://www.wired.com/2012/05/torvalds-github/>

---

# Using Git Locally

Git is a *distributed* version control system, but for this lesson we will use it *locally* (i.e. only on a single computer)

---

# Core Concept: Repository

a *repository* (or "repo") contains the version history a collection of files 

in git, a repo comprises all files and subdirectories inside a single "root" directory

* the command `git init` "blesses" the current directory and makes it into a repo

* the command `git status` describes the state of the current repo

---

# Core Concept: Staging Area

git has a two-step process for tracking changes to files.

* First, you **add** the changes to the *staging area* (also called the *cache* or the *index*)

* Then, you **commit** the changes to the *history* (also called the *log*)

After a commit, the staging area is cleared, and the cycle continues.

Think of the staging area as a loading dock for a warehouse. Boxes (changes) are put there a few at a time, then moved into the warehouse *en masse*.

---

# Core Concept: Commit

After *adding* changes to the staging area, you *commit* them to history.

Confusingly, the term "commit" is both a noun and a verb -- you run "git commit" on the command line to create a "git commit" in the history :-(

When you create a commit, you always provide a *message* describing the nature of the changes:

```
git commit -m 'allow users to change their profile picture'
```

Commit messages are important, and should describe **why** you made the changes. Think of them as journal entries -- without them you will be tracking *what* you changed, but not *why* you made the changes.

---

# Add vs Commit

Q: Why does git have a two-step process for tracking changes? Why doesn't `git add` just add the changes to the history immediately?

A: This lets you tie several related changes together across several files into a single history entry. That single entry is usually related to a *coherent functional change*, with a descriptive *commit message* and clear purpose. 

Think of "git add" as a *rough draft* and "git commit" as a *published version*. "git commit" means "I'm done working for the moment, and I'm ready to share this chunk of work with the team, and discuss it as a single item".

---

# Commit Hash IDs

Every *commit* has a unique *id* (also known as a *hash*), which is a long string of letters and numbers.

    commit d8b95657eebea7083de1a4fb96ba7fb296637342

Fortunately, git allows you to *abbreviate* a hash by using its first few digits... 

...and in fact, git already showed you an abbreviation when you ran `git commit`!

    [master (root-commit) d8b9565] shopping list

Look carefully at the digits inside the brackets -- **`d8b9565`**. They are the *same digits* as the beginning of the full hash above.

> The commit id is generated using a cryptographic algorithm known as "SHA-1 hash", which assures that no two commits will ever have the exact same sequence of digits in their ids. <small><br>(unless someone [tries really hard to force a collision](https://security.googleblog.com/2017/02/announcing-first-sha1-collision.html))</small>

---

# Pushing and Pulling

* Git allows you to *share your code* with other developers.
* If you have a change you want to share, you use the command `git push` 
* If someone else has made a change you want to incorporate into your own repository, you use the command `git pull`
* GitHub.com is a *web site* that allows anyone to create and share git repositories