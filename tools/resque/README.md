# Tools - Resque

[Resque](https://github.com/resque/resque) is a Ruby gem for asynchronously
queueing and running tasks. It stores the tasks in a Redis database, and has
a web front end that can be used to monitor the status of the pending and
previously run tasks.

## Configuration

Adding Resque to a Rails application is pretty straightforward. In the `Gemfile`
add:

```ruby
gem "resque", "~> 1.25.2"
```

At this time, the 2.x branch is not ready for production.

Next add the following to the Rakefile to make the Resque rake tasks available:

```ruby
require "resque/tasks"
task "resque:setup" => :environment
```

For the web front end, add the following to the `config/routes.rb` file:

```ruby
require "resque/server"

resque_web_constraint = lambda do |request|
  current_user = request.env["warden"].user
  current_user.present? #&& current_user.respond_to?(:is_admin?) && current_user.is_admin?
end

Rails.application.routes.draw do
...
  mount Resque::Server.new, :at => "/resque"
```

Uncomment the above line (or modify as necessary) if your User model responds to
`is_admin?` or you have other fine grained permissions implemented.

## Creating and running jobs

Please refer to the
[Resque documentation](https://github.com/resque/resque/tree/5379faa08db53233d7a1bbc4f1e01104be7d7851)
for more information.
