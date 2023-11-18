# [Backstage](https://backstage.io)

The porpuse of this repository is to create an image that allows me to quickly test the main features of Backstage.

## Features
- Added support for `mkdocs-techdocs` (backend docker).
- In-memory database, to avoid config a database (data will be lost every time instance is restarted).

To start the app, run:

```sh
yarn install
yarn dev
```


Example
`app-config.yaml`

```yaml
app:
  title: Backstage Org
  baseUrl: https://backstage.local.domain.com

organization:
  name: My Org

backend:
  baseUrl: https://backstage.local.domain.com
  database:
    client: better-sqlite3
    connection: ':memory:'

auth:
  environment: production

techdocs:
  requestUrl: https://backstage.local.domain.com/api/techdocs
  storageUrl: https://backstage.local.domain.com/api/techdocs/static/docs
  builder: 'local'
  publisher:
    type: 'local'
  generator:
    runIn: local

integrations:
    github:
        - host: github.com
          token: ${GITHUB_TOKEN}

catalog:
  readonly: false
  rules:
    - allow: [Component, API, System, Domain, Resource, Location, Template]
  locations:
    - type: url
      target: https://github.com/Org/repository/blob/main/catalog-info.yaml
```