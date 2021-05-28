Put the `docker-compose.yaml` into a new folder, along with a folder called `/migrations`. Put the sample SQL in there at `/migrations/any-name.sql`. This will seed the MySQL DB on startup.

Run `docker-compose up -d`, and visit Hasura at http://localhost:8080

**Note:** If you would like to a connect to an existing MySQL DB running outside of Docker on `localhost`, you will need to edit the configuration for the Hasura service so that it uses `host` networking. Then use `localhost` for the `--mysql-host` argument. Also, in order for Hasura on `localhost` to connect to the Docker Postgres instance, you'll need to add `5432:5432` to the service `port` configurations for `postgres` so that it's exposed, then change the DB URL to `postgres://postgres:postgrespassword@localhost:5432/postgres`.

```yaml
services:
  graphql-engine:
    # ...
    network_mode: "host"
```

![Query Result](https://i.imgur.com/O5WELkk.png)
"# dockermysql" 
