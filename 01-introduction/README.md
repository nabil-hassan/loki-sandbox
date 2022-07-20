## Loki Introduction

This is a very simple introductory example, which allows you to run a Loki Grafana stack locally, and experiment with log ingestion and querying.

### Using the example

  * Pull the latest Docker images:

```shell
docker compose pull
```

  * Start the stack:

```shell
docker compose up -d
```

  * 

  * Login to Grafana on `http://localhost:3000`, using: `admin/admin` as username/password.

### Explaining the configuration

The configuration for Loki and Promtail is found in the files [loki.yml](./loki/loki.yml) and [promtail.yml](./promtail/promtail.yml) accordingly.

The folders containing these files are mounted as Docker volumes, so they are accessible to the respective containers at runtime.

#### Promtail

The key parts of the Promtail config file are:

* The `clients` element, which informs Promtail to push logs to Loki.
* The `scrape_configs`, which informs Promtail to look at files ending in `.log`, that are found in the [logs](./logs) folder.