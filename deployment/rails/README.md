# Deployment - Rails

## Exception tracking

The tool we use to track unhandled exceptions within a Rails application is
[Sentry](http://sentry.readthedocs.org/).

In the following example, the Sentry client Raven is being configured to run in
the staging and production environments for a Rails application.

require the `sentry-raven` gem in the `Gemfile`

```ruby
gem "sentry-raven",
    git: "https://github.com/getsentry/raven-ruby.git",
    tag: "0.12.3"
```

add the following to `config/initializers/raven.rb`

```ruby
require "raven"

Raven.configure do |config|
  config.environments = %w( staging production )
  dsn = Rails.application.config.try(:sentry_dsn)
  config.dsn = dsn if dsn
end
```

In each environment (**not in version control**), add the following to the
`config/environments/[environment].rb` file within the
`Rails.application.configure do` block

```ruby
config.sentry_dsn = "https://sentry.example.com"
```

The actual DSN URL can be found under **Settings** > **API Keys** within a
project in the Sentry web application.
