# Database Testing

Loadmill allows users to execute various queries directly to their DB in order to validate data. This is a very powerful feature as it allows users to check data integrity and accuracy.

### Usage

#### Postgres

To execute a database query:

1. Go to the relevant test flow within your Test Suite.
2. Request Method: POST.
3. Request URL: `https://db-relay-service.loadmill.com/api/postgres`
4. Content Type: application/json
5. Request Body:

```json
body: {
  "connectionString": "postgres://...",
  "query": "SELECT * FROM USERS"
}
```

See the request example below:

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Running this request with result with a JSON response with the required data.

#### MongoDB

To execute MongoDB queries:

1. Apply the same steps above.
2. Request URL: `https://db-relay-service.loadmill.com/api/mongo`
3. Request Body:&#x20;

{% hint style="success" %}
In this example we're searching for a user with the name "John"
{% endhint %}

```json
body: {
  connectionString: 'mongodb://...',
  collection: 'users',
  command: 'find',
  query: { "name":"John" }
}
```

{% hint style="info" %}
The MongoDB service is initially meant for "read-only" purposes (i.e. find). However, using a Docker image privately allows you to use the environment variable `ALLOW_ALTERING=true` and by doing so the following options are available:\
`insertOne`, `insertMany`, `updateOne`, `updateMany`, `deleteOne` and `deleteMany`.
{% endhint %}

#### MongoDB Altering Example Options

**InsertOne:**

```json
body: {
  connectionString: 'mongodb://...',
  collection: 'users',
  command: 'insertOne',
  query: { "name": "John", "age": "56" }
}
```

**updateOne:**

```json
body: {
  connectionString: 'mongodb://...',
  collection: 'users',
  command: 'updateOne',
  query: { "name":"John" },
  update: { "$set": { "age": "67" } }
}
```

**deleteOne:**

```json
body: {
  connectionString: 'mongodb://...',
  collection: 'users',
  command: 'deleteOne',
  query: { "name":"John" }
}
```

Additional help regarding update operators can be found [here](https://www.mongodb.com/docs/manual/reference/operator/update).

#### Redis

To execute Redis queries:

1. Apply the same steps above.
2. Request URL: `https://db-relay-service.loadmill.com/api/redis`
3. Request Body:&#x20;

<pre class="language-json"><code class="lang-json"><strong>body: {
</strong>  {
    connectionString: "redis://...", 
    command:"get | hget | hgetall",
    key:"any-key",
    field: "any-field"
   }
}
</code></pre>

#### MySQL

To execute queries directly to MySQL 5.7:

1. Apply the same steps above.
2. Request URL: `https://db-relay-service.loadmill.com/api/mysql`
3. Request Body:&#x20;

```json
body: {  
  "connectionString": "mysql://...",
  "query": "SELECT * FROM TASKS"
}
```

### DB relay service static IPs

Executing queries to your environment DB may require VPN. You can easily overcome this by whitelisting the DB relay service static IPs: `[52.42.51.230, 54.190.108.53]` in your firewall.

### Docker image

You can use a Docker image for DB relay service to deploy it in a specific environment.

&#x20;Find more information [here](https://hub.docker.com/r/loadmill/db-relay-service).
