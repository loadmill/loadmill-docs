# Loadmill DB relay service

Loadmill provides a service that allows users to execute various queries directly to their DB in order to validate data.

## Usage

### Postgres

To execute a query:

1. Go to a relevant test flow within a Test Suite.
2. Select "POST" as request Method, put URL - `https://db-relay-service.loadmill.com/api/postgres`
3. Choose "application/json" as Content-type.
4. Put the request body with the following structure:

```text
body: {
  connectionString: 'postgres://...',
  query: 'SELECT NOW()'
}
```

See a request example below:

![](../.gitbook/assets/screen-shot-2021-02-25-at-16.17.02.png)

By running the request, you will get a response in JSON format. 

### MongoDB

Execute queries directly to MongoDB:

`https://db-relay-service.loadmill.com/api/mongo`

```text
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

```text
body: {
  {
    connectionString: "redis://...", 
    command:"get | hget | hgetall",
    key:"any-key",
    field: "any-field"
   }
}
```

### 

