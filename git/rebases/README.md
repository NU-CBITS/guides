# Git - Rebases

While you work on your local branch, others may be commiting to `origin/master`
in which case your push will fail due to merge conflicts. One strategy to avoid
this is rebasing.

```
git fetch
git rebase origin/master
```

There will still occasionally be conflicts to resolve, but this will prevent a
lot of them, and leave a cleaner commit log.
