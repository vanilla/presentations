# Splitting and merging repos using git

![](https://leanpub.com/site_images/git-flow/git-workflow-gitflow.png)

---

## Objective

https://github.com/vanilla/vanilla/issues/7880

We are going to be moving the `debugbar` from `internal` into `addons`.

---

## Preparing the `internal` Repo

We want a branch that:

- Contains only the following directory: `/plugins/debugbar`.
- Contains only commits related to that directory.
- Will have no merge conflicts if we try to merge it to the `vanilla` repo.

---

## Preparing the `internal` Repo

```sh
# Verify that we have nothing in progress
cd /git/srv/internal
git checkout master
git status
```

---

## Preparing the `internal` Repo

*Be 100% sure you have nothing special on you local master branch*

```sh
git filter-branch -f --prune-empty --subdirectory-filter plugins/debugbar/ @
```

---

## Preparing the `internal` Repo

This will have rewritten your git history as if that subdirectory `/plugins/debugbar` were
its own repository. This means all files will be at the top level.

Use terminal or your IDE to

- Create a new /plugins/debugbar directory
- Move _everything_ into it.
- Commit this.

---

## Creating a branch and resetting master

```sh
# Save our work
git checkout -b feature/move-debugbar

# Fixup master
git checkout master
git reset --hard origin/master
```

---

### Merging the repos

```sh
# Move into addons
cd ../addons
git checkout master
git status

# Checkout a new branch
git checkout -b feature/move-debugbar

# Add local remote
git remote add local/internal ../internal
git fetch local/internal
```

---

### Doing the merge

```sh
git merge --allow-unrelated-histories local/internal/feature/move-debugbar
```

---

### Make PRs

Now open a pull request.

---

## Further Reading

- `man git merge`
- `man git filter-branch`
