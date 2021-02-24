---
description: Enable customers to execute queries directly to their DB
---

# Loadmill DB relay service

### Usage

Execute queries directly to Postgres:

[https://db-relay-service.loadmill.com/api/postgres](https://db-relay-service.loadmill.com/api/postgres)

```text
body: {
  connectionString: 'postgres://...',
  query: 'SELECT NOW()'
}
```

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

### Usage

Build docker image:

```text
docker build -t db-relay-service .
```

Build docker container:

```text
docker run -it -p 8080:8080 db-relay-service
```

Stop docker container:

```text
docker ps 
docker stop ${CONTAINER ID}
```

