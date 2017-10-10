# Development - Rails - Database Setup

## Applications & Host Applications

### Creating & Migrating the Database

In order to use structure.sql, in `config/application.rb`

```
Rails.application.configure do
  config.active_record.schema_format = :sql
end
```

For apps or host applications, set up the database:

```
rails db:setup
```

On subsequent builds, you will need to run

```
rails db:reset
```

### Seeding the Database

Update the `seeds.rb` file by creating necessary data using factories:

```ruby
# db/seeds.rb

require "factory_girl"

USER_COUNT = 1

def seed_development
  puts "Seeding development data."

  FactoryGirl.create_list :user, USER_COUNT
end

if Rails.env.development?
  seed_development
end
```

Once the `seed.rb` file has been updated, seed the database:

```
rake db:seed
```

## Engines

### Creating & Migrating the Dummy App Database

For engines, setting up the database is similar but the rake commands are
namespaced with `app`:

```
rake app:db:drop app:db:create app:db:migrate
```

### Seeding the Dummy App Database

Update the `seed.rake` file by creating a `seed:with_[engine_name]_fixtures`
rake task. Within this task, add the necessary fixture paths (i.e., file names):

```ruby
# lib/tasks/seed.rake

require "active_record/fixtures"

namespace :seed do
  desc "seed the database with fixtures from spec/fixtures"
  task with_engine_name_fixtures: :environment do
    path = File.join(File.dirname(__FILE__), "..", "..", "spec", "fixtures")
    ActiveRecord::FixtureSet.create_fixtures path, [
      :fixture_file_1,
      :fixture_file_2,
      :fixture_file_3
      ...
    ]
  end
end
```

Note however, that the rake task name includes the engine's name: ```with_[engine_name]_fixtures```.

Once the ```seed.rake``` file has been updated, seed the database with fixtures:

```
rake app:seed:with_[engine_name]_fixtures
```
