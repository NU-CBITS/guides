# Development - New projects

When setting up a new project, the following **must** be configured before
development and deployment can proceed:

* GitHub repository/repositories
  * Pivotal Tracker webhook
* Travis CI
* Slack channel

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
* code coverage report
