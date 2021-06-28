# LAB: branch

We will now pretend to be planning a party. We want to think about the party favors for a while before *merging* them into the main shopping list.

1. enter your Shopping List repo

        cd shopping
2. create a new branch called `party`

        git checkout -b party
3. in this branch, add a few party items (like cake or booze) to the list using your text editor
4. make a *commit* on this branch containing the party items

        git add .
        git commit -m "party stuff"
5. *switch back* to master. Notice that the party items are now **gone**.

        git checkout master

6. *switch back and forth* a few times and see the party items reappear and disappear

# LAB: merge

* **on master**, add some other non-party-related items to the list, and *make a new commit* with these items
* **merge** your party branch into master
* there will probably be conflicts. **Don't panic!**
* in a text editor, resolve the conflicts
* when you're satisfied, **finish the merge** with `git add` and `git commit`

> with merges, it's usually best to run `git commit` **without** *a message* since git fills in a good message for merges already. This will open the message in a console text editor, usually `vi`. If it looks good, exit `vi` by typing `:q!` 

* finally, run `git log --graph` to see your commit history with a little ASCII art diagram of the branches diverging and converging