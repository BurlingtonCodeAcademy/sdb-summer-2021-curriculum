# Git

**git** is a distributed version control tool.

Developer teams use it to keep track of project changes and switch between different versions.

We can track the following:

- A log of changes to the files
- Including _who_ made each change
- And _why_ they made that change

How do you think this tool helps developers and their companies?

---

# Git vs GitHub

[GitHub](https://github.com/) is a hub for software versions managed using git. You can think of it as a social network (hub) where people share their code (git).

There are other options than GitHub like GitLab and BitBucket, but GitHub is the most popular and accessible by far.

---

# Core Concept: Repository

A **repository** (or "repo") contains all of the versions of a project.

A repo is always held in a single directory.

- `git init` (short for initialize) makes the current directory a _repository_ that you can now track.

- `git status` lists the changes that have been tracked in the _repository_.

---

# Core Concept: Staging Area

git has a two-step process for tracking changes to files.

- First, you **add** the changes to the _staging area_ (also called the _cache_ or the _index_)

- Then, you **commit** the changes to the _history_ (also called the _log_)

After a commit, the staging area is cleared, and the cycle continues.

Think of the staging area as a loading dock for a warehouse. Boxes (changes) are put there a few at a time, then moved into the warehouse _en masse_.

---

# Core Concept: Commit

After `add`ing changes, they are stored in a `staging` area. When ready to save the changes, you `commit` them.

When `commit`ing, you always provide a _message_ describing _why_ the changes are there (not a summary).

```sh
git commit -m "Allow Users to Change Their Profile Picture"
```

Without commit messages, you will be tracking _what_ you changed, but not _why_ you made the changes.

---

# Commit Hash IDs

Every _commit_ has a unique _ID_ (also known as a _hash_), which is a long string of letters and numbers.

`commit d8b95657eebea7083de1a4fb96ba7fb296637342`

Fortunately, git allows you to _abbreviate_ a hash by using its first few digits...

...and in fact, git shows this when using `git commit`!

`[master (root-commit) d8b9565] shopping list`

Look carefully at the digits inside the brackets -- **`d8b9565`**. They are the _same digits_ as the beginning of the full hash above.

---

# Sharing Code

- To _upload_ your changes _to_ GitHub, you use the command:

```sh
git push

# alternatively, to a specific repository and branch
git push origin master
```

- To _download_ changes _from_ GitHub, you use the command:

```sh
git pull

# alternatively, from a specific repository and branch
git pull origin master
```
