# LAB: Branch Party

Let's practice creating a switching between branches by planning a party! What items do you think we will need? Can they be grouped into different categories?

1. Create a subdirectory in your code folder called `shopping`. Enter it and initialize it as a git repository.

```javascript
mkdir shopping
cd shopping
git init
```
2. Create a new branch called `party` and a new file called `list.txt`. Add and commit this file.
```javascript
git checkout -b party
touch list.txt
git add .
git commit -m"let's get this party started!"
```

3. Open VS Code to access the list. Create a new branch called `food` and type in some food for the party (like cake or ice cream).

```javascript
code .
git checkout -b food
```

3. When you're done, make a *commit* on this branch containing the food items.

```javascript
git add .
git commit -m "food items"
```

3. Head back to the `party` branch. Notice that the food items are now gone.

```javascript
git checkout party
```

4. From `party`, create a new branch called `gifts` and enter some presents that you want to bring (or receive!).
```javascript
git checkout -b gifts
```

5. When you are ready, make a commit.

```javascript
git add .
git commit -m "presents added"
```

6. Head back to the `party` branch again. Try this new command to see your branches. The one with the '*' next to it indicates which branch you are on.

```javascript
git checkout party
git branch
```

7. Switch back to your food list and add some more items
```javascript
git checkout food
```
Don't forget to commit when complete!

8. And then head to gifts and edit this list, too.
```javascript
git checkout gifts
```
Commit this, too.

Notice how your changes are saved between branches, and the items exist on the branches alone? Cool!