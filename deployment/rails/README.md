# Deployment - Rails

## Exception tracking

The tool we use to track unhandled exceptions within a Rails application is
[Sentry](http://sentry.readthedocs.org/).

In the following example, the Sentry client Raven is being configured to run in
the staging and production environments for a Rails application.

require the `sentry-raven` gem in the `Gemfile`

```
group :staging, :production do
  gem "sentry-raven",
      git: "https://github.com/getsentry/raven-ruby.git",
      tag: "0.12.3"
end
```

add the following to `config/initializers/raven.rb`

```
if Rails.env.staging? || Rails.env.production?
  require "raven"

  Raven.configure do |config|
    config.dsn = Rails.application.config.sentry_dsn
  end
end
```

On staging, add the following to the `config/environments/staging.rb` file
within the `Application.configure do` block

```
config.sentry_dsn = "https://sentry.example.com"
```

The actual DSN URL can be found under **Settings** > **API Keys** within a
project in the Sentry web application.
