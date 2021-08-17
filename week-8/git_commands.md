# Common Commands

---

# List all branches in your repository

```javascript
git branch 
```

---
# Create a new branch and checkout to it

```javascript
git checkout -b branch_name
```

---

# Switch between branches

```javascript
git checkout branch_name
```

---

# Confirm branch status

```javascript
git status
```

---
 
# Prepare branch for push

```javascript
git add .
git commit -m “commit message”
```

---

# Git push:


```javascript
git push
```

Or if pushing to a remote repository:
```javascript
git push -u origin branch_name
```

---
 
# Git merge...

...on the receiving branch after the branch to-be-merged has been added, committed, and pushed:
```javascript
git merge branch_name
```

---
 
# “Safe” branch deletion

Prevents you from deleting a branch if it has unmerged changes:
```javascript
git branch -d branch_name
```

---
 
# Bring updated codebase down...

....to your local machine:
```javascript
Git pull
```

---
 

# Deletes a branch...

...regardless of it’s merge status

```javascript
git branch -D branch_name
```

---
 
# Rename branch

```javascript
git branch -m new_branch_name
```
