# Bazaar

[![CircleCI Build Status](https://circleci.com/gh/naamancurtis/bazaar.svg?style=shield)](https://app.circleci.com/pipelines/github/naamancurtis/bazaar)

## Docker

```sh
docker build --tag bazaar --file Dockerfile .
docker run -p 8000:8000 bazaar
```

## Tooling

| Name                                                                 | Purpose                                        | Installation                                    |
| -------------------------------------------------------------------- | ---------------------------------------------- | ----------------------------------------------- |
| [SQLx CLI](https://github.com/launchbadge/sqlx/tree/master/sqlx-cli) | Database Migrations                            | `cargo install --version=0.2.0 sqlx-cli`        |
| [PSQL](https://formulae.brew.sh/formula/libpq)                       | Used predominately for the utilities of `psql` | `brew install libpq && brew link --force libpq` |

## Database Migrations

### Creating Migrations

```sh
# Ensure $DATABASE_URL is correctly set
sqlx migrate add <migration name>
```

### Running Migrations

These are set up to run manually with `./scripts/init_db.sh`, optionally you can
pass a skip variable if a docker instance is already running `SKIP_DOCKER=true ./scripts/init_db.sh`

If you need to run them manually, you can do so with the sqlx CLI:

```sh
sqlx migrate run
```

### Preparing for SQLX offline

```sh
cargo sqlx prepare -- --bin app
```
