# DDEV-postgres

- [DDEV-postgres](#ddev-postgres)
  - [Setup](#setup)

## Setup
- Install laravel

```bash
$ laravel new ddev-postgres
$ php artisan --version
Laravel Framework 8.61.0
```

- Install DDEV, accept defaults

```bash
$ ddev config
$ ddev --version
ddev version v1.17.7
```

- Copy `docker-compose.postgres.yaml` to `.ddev`
- Copy `commands/postgres` directory to your project's `.ddev/commands`

- Update `.env`

```env
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=db
DB_USERNAME=db
DB_PASSWORD=db
```

- Attempt to migrate database

```bash
$ ddev artisan migrate:fresh
...
Migration table created successfully.
```

- This confirms that Laravel has been successfully setup to use Postgres via DDEV.
- Note: There is no `.ddev/import-db` folder present. Current installation have no mention of creating one.

- Run `ddev pgsql_export`

```bash
$ ddev pgsql_export
bash: /mnt/ddev_config/import-db/postgresql.db.sql: Permission denied
Failed to run pgsql_export : exit status 1
```

- Note: There is now a `.ddev/import-db` folder present.
```bash
$ ls -la ./.ddev
drwxr-xr-x 14 dev       dev       4096 Sep 27 10:00 .
...
drwxr-xr-x  2 root      root      4096 Sep 27 10:00 import-db
```
