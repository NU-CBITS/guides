# Patterns - Rails

## Recurring tasks/jobs

Our go-to tool for this is basically just a wrapper for cron.
[Whenever](https://github.com/javan/whenever) involves a configuration file
such as this:

```ruby
set :output, "#{path}/log/cron.log"

every 1.day, at: "9:00am" do
  rake "reminders:app_use_reminder"
end
```

along with a rake task that will load up the Rails environment when it runs and
thus can depend on Rails application classes and the database.
