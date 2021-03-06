# Git Branching Work-flows

* When working in Git you will find using branches helpful
* Branches are a core part of Git and can make working with others easier
* There are several *general* strategies for using branches

---

# Branch Basics

* Branches are a lightweight tool for managing change in Git
* **`master`** is the name of the default branch
* a branch always points to a commit 
    * which could point to other commits recursively
    * eventually all branches point back to some spot on `master`
    * other branches contain all the changes since they diverged from `master`

---

# Example: Branch Basics Diagram

![Branch Basics Diagram](/images/git-branch-basics.png "Branch Basics Diagram")

---

# Branching Commands

|command|description|
|---|---|
|`git checkout -b x` | create a new branch named `x` based off the current commit |
|`git checkout x` | switch to the branch named x |
|`git branch` | list all known branches |
|`git merge x` | *merge* branch x into the current branch |

---

# Git Merge

* `git merge` takes a branch and connects it to another
  * usually you merge *to and from* `master` into a *feature branch*

* to *merge* is to create a *new commit* on the current branch
  * that "merge commit" has two parents, and represents all changes from both branches

---

# Merge Conflicts

If there are merge conflicts, resolve them. This is a manual process and can be frustrating and confusing. The basic rule is that if there is a conflict, you need to look for lines like this:

```
<<<<<<<<<<<<<<<<
foo
----------------
bar
>>>>>>>>>>>>>>>>
```

and then manually edit the files until all the chevrons and dashes are gone, and what's left is correct. In this example, you might choose `foo` or `bar`, or `foobar`, or `bar + foo`, or something altogether different. Then `git add` the corrected file and follow the instructions on the console to finish the merge.

---

# Merge Conflicts (cont.)

As a more realistic example of a conflict:

```
<<<<<<<<<<<<<<<<
Hours: M-F open at 9, closed weekends
----------------
Hours: 9:00 am to 5:00 pm
>>>>>>>>>>>>>>>>
```

This example shows why git *cannot* automatically resolve intra-line conflicts. As a human, you are the only one capable of making this sort of *semantic* choice. You must decide whether this file would be better off with one or the other or a creative combination of both changes, and you should communicate with other humans about this decision, in the GitHub discussion thread or face-to-face.

---

# Branching Strategies

* Different teams will choose different strategies for managing their branches.
* A branching strategy is also called a "workflow"
  * one popular strategy is named "Git Flow" but it's not the only git flow

---

# Long Running Branches

* This strategy uses two or more branches that are periodically **merged** into the **master** branch.
* In this strategy, once you merge a change `master` you are saying "this change is ready for testing and deployment"

---

## Pros

* Simple
* Consistent
* Low cognitive overhead


## Cons

* Conflicts between **master** and the **other** branches
* Need to keep long running branches to a minimum

---

# Example: Master <- Develop

* Using the **master** branch as **stable**
* And using the **develop** branch as **experimental**

Using this strategy, you would **merge** the **development** branch into **master** when you want to activate the new features.

---

# Example: Long Running Diagram

![Long Running Branches](/images/long-running-branches-many.png "Long Running Branches")

---

# Example: Long Running Code

```shell
$ git checkout master
$ git status

On branch master
Your branch is up-to-date with 'origin/master'.

$ git branch develop
$ git checkout develop
$ git add files_that_changed
$ git commit -m "My awesome changes"
$ git checkout master
$ git pull
$ git merge develop
$ git push origin/master
```

---

# Feature Branches

* Feature branches are short lived and focus on **one** feature at a time
* They should be branched off the updated **master** and be merged quickly

---

## Pros

* Isolated code changes
* Easy to merge when used as designed
* Leaves a trace about the intent of the branch

## Cons

* Can clutter the history
* Need to be disciplined about keeping feature branches *focused* and *short-lived*

---

# Master <- Feature

* Using **master** branch as **stable**
* And using a new **topic** or **feature** branch as **experimental**

---

# Example: Feature Branch Diagram

![Topic Branches with Merge](/images/topic-branches-merged.png "Topic Branches with Merge")

---

# Example: Feature Branches Many

![Topic Branches Many](/images/topic-branches-git.png "Topic Branches Many")

---

# Continuous Delivery

* Some teams merge new features directly to master
* After every commit, the code is automatically...
  * tested
  * deployed
* This flow depends on a solid, stable set of automated tests
* Benefits from *feature flags* which can switch new features on and off

<https://martinfowler.com/bliki/ContinuousDelivery.html>
