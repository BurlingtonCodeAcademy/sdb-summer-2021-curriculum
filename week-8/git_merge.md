# Merge Conflicts

A merge conflict can arise when developers make changes to the same content, or one developer deletes a file that another developer was editing, and then these 

------------------- Because these changes happen in feature branches, we can resolve them fairly easily.

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

# LAB: Git merge resolution