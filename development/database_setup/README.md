# Development - Database Setup

## Applications & Host Applications

### Creating & Migrating the Database

For apps or host applications, set up the database:
```
rake db:drop db:create db:migrate
```

### Seeding the Database

Update the ```seed.rake``` file by creating a ```seed:with_fixtures``` rake task.  Within this task, add the necessary fixture paths (i.e., file names):

```ruby
# lib/tasks/seed.rake

require "active_record/fixtures"

namespace :seed do
  desc "seed the database with fixtures from spec/fixtures"
  task with_fixtures: :environment do
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

Once the ```seed.rake``` file has been updated, seed the database with fixtures:
```
rake seed:with_fixtures
```

Note: When a new fixture file is added, it won't seed the database unless it is added to the list of fixture paths within the ```seed.rake``` file.

## Engines

### Creating & Migrating the Database

For engines, setting up the database is similar but the rake commands are namespaced with ```app```:
```
rake app:db:drop app:db:create app:db:migrate
```
### Seeding the Database

Update the ```seed.rake``` file by creating a ```seed:with_[engine_name]_fixtures``` rake task.  Within this task, add the necessary fixture paths (i.e., file names):

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