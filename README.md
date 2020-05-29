# Rust on Rocket MicroService

Skeletal fullstack MicroService built with Rust on [Rocket](http://rocket.rs/), backed by Postgres, including CRUD operations, authentication (JWTs), routing, pagination, and more.

Adheres to the [Rocket](http://rocket.rs/) styleguides & best practices.

## CHANGELOG

Eventual [CHANGELOG](CHANGELOG.md). Not much here yet.

## Setup

Install [nightly](https://www.rust-lang.org/en-US/install.html)

```sh
# Install RustUp
$ curl https://sh.rustup.rs -sSf | sh

rustup install nightly

# Start Postgres and seed it:
$ psql -f init.sql postgres://postgres:password@localhost:32768
# Non-default port pointing to Postgres in a Container. ^
# Omit and it will connect on 5432.

$ cargo install diesel_cli --no-default-features --features "postgres"

# Run migrations.
$ diesel migration run

# Start the web server.
$ cargo run
```

## Tests

```sh
$ cargo test
```

You can also check postman/newman. See `/tests` directory.

## DB Connection

`diesel` cli uses `.env` file. Rocket sets database configuration from `.env` file.
Rocket's [Guide](https://rocket.rs/guide/) here.

## Slugs

The "random suffixes" feature is enabled which appends a random slug onto the URL,
so article-title collisions are avoided. To disable it:

```sh
$ cargo run --no-default-features
```

## Routes

![ss-routes](https://user-images.githubusercontent.com/214047/83105279-604ee100-a088-11ea-921e-e65ba2ab85b7.png)

## TODO

1. Bettter Error handling
1. Containerize / IAC: Docker Compose / Kube
2. More functionality
