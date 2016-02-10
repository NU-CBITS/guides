# CBITS developer guides

Documentation of the CBITS development process.

Thanks to the [Thoughtbot guides](https://github.com/thoughtbot/guides) for
inspiration.

* [deployment](/deployment)
  * [Mobile applications](/deployment/mobile_apps)
  * [Rails](/deployment/rails)
* [development](/development)
  * [AngularJS](/development/angular)
  * [code reviews](/development/code_reviews)
  * [Cordova](/development/cordova)
  * [estimation](/development/estimation)
  * [iOS](/development/ios)
  * [new projects](/development/new_projects)
  * [postgres](/development/postgres)
  * [Rails](/development/rails)
    * [database schema](/development/rails/database_schema)
    * [database setup](/development/rails/database_setup)
  * [releases](/development/releases)
* [examples](/examples)
* [git](/git)
  * [commits](/git/commits)
  * [pull requests](/git/pull_requests)
  * [rebases](/git/rebases)
* [testing](/testing)
  * [Appium](/testing/appium)
  * [JavaScript](/testing/javascript)
  * [RSpec](/testing/rspec)
  * [Selenium](/testing/selenium)
    * [Selenium IDE](/testing/selenium/selenium_ide)
    * [Selenium WebDriver](/testing/selenium/selenium_webdriver)
* [tools](/tools)
  * [android](/tools/android)
  * [hockeyapp](/tools/hockeyapp)
  * [npm](/tools/npm)
  * [resque](/tools/resque)

## Contributing

clone the repository

```
git clone git@github.com:cbitstech/guides.git
```

install dependencies

```
bundle
```

run the Markdown lint tool as you work. For mdl rules see:
[Rules](https://github.com/mivok/markdownlint/blob/master/docs/RULES.md)

```
rake
```

make edits, [commit](/git/commits) and [rebase](/git/rebases) often, then
[submit a pull request](/git/pull_requests)
