---
title: Delete merged branches
tags: repository,branch,advanced
---

Deletes all local merged branches.

- Use `git branch --merged <branch>` to list all branches merged into `<branch>`.
- Use the pipe operator (`|`) to pipe the output and `grep -v "(^\*|<branch>)"` to exclude the current and the target `<branch>`.
- Use the pipe operator (`|`) to pipe the output and `xargs git branch -d` to delete all of the found branches.

```sh
git branch --merged <branch> | grep -v "(^\*|<branch>)" | xargs git branch -d
```

```sh
git checkout master
git branch
# master
# patch-1
# patch-2

# Assuming `patch-1` is merged into master
git branch --merged master | grep -v "(^\*|master)" | xargs git branch -d

git branch
# master
# patch-2
```