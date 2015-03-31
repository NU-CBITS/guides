# Development - New projects

When setting up a new project, the following **must** be configured before
development and deployment can proceed:

* GitHub repository/repositories
  * Pivotal Tracker webhook
* Travis CI
* Slack channel

## Repository conventions

All repositories **must** be named using "snake case". All installable
applications **must** have the `_app` suffix, and all web applications that
serve mostly administrative purposes **must** have the `_dashboard` suffix.

Prototypes or demonstrations that are associated with production applications
**must** be on a repository branch called `prototype`.

## Rails

The following **must** be run as part of the `rake` task:

* RuboCop
* Brakeman
* RSpec test suite
* SimpleCov

## Cordova

All dependencies aside from those that are platform specific or installable only
via GUI **must** be installable via `npm install`.

The project **must** be built via the command `npm build`.

The following **must** be run as part of the `npm test` task:

* linting (preferably [ESLint](http://eslint.org/))
* unit and feature test suites
