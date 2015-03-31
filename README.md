# CBITS developer guides

Documentation of the CBITS development process.

Thanks to the [Thoughtbot guides](https://github.com/thoughtbot/guides) for
inspiration.

* [development](/development)
  * [code reviews](/development/code_reviews)
  * [new projects](/development/new_projects)
  * [releases](/development/releases)
* [git](/git)
  * [commits](/git/commits)
  * [pull requests](/git/pull_requests)
  * [rebases](/git/rebases)
* [tools](/tools)
  * [npm](/tools/npm)
* [testing](/testing)
  * [Appium](/testing/appium)
  * [RSpec](/testing/rspec)

## Contributing

clone the repository

```
git clone git@github.com:cbitstech/guides.git
```

install dependencies

```
bundle
```

run the Markdown lint tool as you work

```
rake
```

make edits, [commit](/git/commits) and [rebase](/git/rebases) often, then
[submit a pull request](/git/pull_requests)
