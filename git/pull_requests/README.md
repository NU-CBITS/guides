# Git - Pull requests

When you want to make a contribution to a repository, start by creating a new
local branch.

```bash
git checkout -b <initials>_<JIRA Key>_<blurb>
```

Here, `<initials>` are your initials, `<JIRA Key>` is the identifier of the
story in JIRA and `<blurb>` is 1-3 words related to the topic of the
pull request.

For example

```bash
git checkout -b cbt_RC-22_superfluous_words
```

When satisfied, commit your changes then check for updates and rebase. Finally,
push your changes.

```bash
git commit -v
git fetch
git rebase origin/master
git push origin head
```

Here, the `-v` or `--verbose` flag opens the commit message editor with a diff
of all your changes for review.

Lastly, open a pull request on GitHub. Navigate to the repository in a browser
and you will see big friendly buttons that allow you to open the request.
