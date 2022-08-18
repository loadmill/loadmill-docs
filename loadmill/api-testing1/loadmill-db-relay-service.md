# DB Testing using Queries

Loadmill provides a service that allows users to execute various queries directly to their DB in order to validate data.

## Usage

### Postgres

To execute a query:

1. Go to a relevant test flow within a Test Suite.
2. Select "POST" as request Method, put URL - `https://db-relay-service.loadmill.com/api/postgres`
3. Choose "application/json" as Content-type.
4. Put the request body with the following structure:

```
body: {
  "connectionString": "postgres://...",
  "query": "SELECT * FROM USERS"
}
```

See a request example below:

![](../../.gitbook/assets/screenshot-2021-10-03t153602.437.png)

By running the request, you will get a response in JSON format and be able to operate the data.

### MongoDB

Execute queries directly to MongoDB:

`https://db-relay-service.loadmill.com/api/mongo`

```
body: {
  connectionString: 'mongodb://...',
  collection: 'bios',
  command: 'find',
  query: { "awards.award": "Turing Award" }
}
```

### Redis

Execute queries directly to Redis:

`https://db-relay-service.loadmill.com/api/redis`

```
body: {
  {
    connectionString: "redis://...", 
    command:"get | hget | hgetall",
    key:"any-key",
    field: "any-field"
   }
}
```

### MySQL&#x20;

Execute queries directly to MySQL 5.7:

`https://db-relay-service.loadmill.com/api/mysql`

```
body: {  
  "connectionString": "mysql://...",
  "query": "SELECT * FROM TASKS"
}
```

## DB relay service static IPs

Sometimes, executing queries to your env DB may require VPN. You can easily avoid this by whitelisting the DB relay service static IPs: \[52.42.51.230, 54.190.108.53] in your firewall.

## Docker image

You can also use a docker image for DB relay service to deploy it in a specific environment of yours, find more information [here](https://hub.docker.com/r/loadmill/db-relay-service).
