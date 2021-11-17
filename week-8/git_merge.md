# Merge Conflicts

A merge conflict can arise when developers make changes to the same content, or one developer deletes a file that another developer was editing, and then these 

If these changes happen in feature branches, we can resolve them fairly easily, and without worrying about breaking our main branch.

---

# Merge Conflict Resolution

This is a manual process that can be frustrating and confusing. The basic rule is that if there is a conflict, look for lines that appear like this:

```
<<<<<<<<<<<<<<<<<<<<
Foo
--------------------
Bar
>>>>>>>>>>>>>>>>>>>>
```

And then manually edit the files until all chevrons and dashes are gone, and what’s left is correct. In this example you might choose `foo` or `bar`, or `foobar`, or `bar + foo`, or something altogether different. Then `git add .` the corrected file and follow the instructions on the console to finish the merge.

---

# Rebasing

Another way of combining branches is to *rebase* onne branch on top of another. Rebasing works a lot like merging except it stacks the commits from the branch you're in on top of the commits from the branch you're rebasing onto rather than weaving the commits together based on the time of the commit (like a merge does).

A common practice is to rebase your feature branch on top of your master branch, and then merge the feature branch on top of the master branch. This keeps your commit history clean, and helps guard against regression.

It's as easy as 1 -2 - 3! From a branch named `feature_branch`, after adding and committing your changes:

1. `git rebase master`
2. `git checkout master`
3. `git merge feature_branch`