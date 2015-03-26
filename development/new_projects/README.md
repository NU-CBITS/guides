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

The following **must** be run as part of the `npm test` task:

* JSHint
* unit and feature test suites
