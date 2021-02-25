# Loadmill DB relay service

Loadmill allows users to execute queries directly to their DB in order to validate data.

## How it works

### Postgres

Execute queries directly to Postgres:

1. Go to a relevant test flow within a Test Suite.
2. Select "POST" as Method, put URL - [https://db-relay-service.loadmill.com/api/postgres](https://db-relay-service.loadmill.com/api/postgres)
3. Put the request body with a structure:

```text
body: {
  connectionString: 'postgres://...',
  query: 'SELECT NOW()'
}
```

See a request example below:

![](../.gitbook/assets/screen-shot-2021-02-25-at-16.17.02.png)

### MongoDB

Execute queries directly to MongoDB:

[https://db-relay-service.loadmill.com/api/mongo](https://db-relay-service.loadmill.com/api/mongo)

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

[https://db-relay-service.loadmill.com/api/redis](https://db-relay-service.loadmill.com/api/redis)

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

