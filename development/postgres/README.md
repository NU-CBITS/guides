# Development - Postgres

## Configuring pg gem

* First, check the value of your Postgres config path

```
sudo find / -name "pg_config"
```

* Install the pg gem with the configuration path found with previous
  command. Example:

```
gem install pg -- --with-pg-config=/Applications/Postgres.
app/Contents/Versions/9.3/bin/pg_config
```

* If you continue to receive errors upon installing the pg gem, try something
  like the following:

```
env ARCHFLAGS="-arch x86_64" gem install pg -- --with-pg-
config="/Applications/Postgres.app/Contents/Versions/9.3/bin/pg_config"
```
