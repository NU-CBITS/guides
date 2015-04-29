# Development - Postgres

## Configuring pg gem

1. First, check the value of your Postgres config path

```
sudo find / -name "pg_config"
```

1. Install the pg gem with the configuration path found with previous
  command. Example:

```
sudo gem install pg -- --with-pg-config=/Applications/Postgres.
app/Contents/Versions/9.3/bin/pg_config
```

1. If you continue to receive errors upon installing the pg gem, try something
  like the following:

```
sudo env ARCHFLAGS="-arch x86_64" gem install pg -- --with-pg-
config="/Applications/Postgres.app/Contents/Versions/9.3/bin/pg_config"
```