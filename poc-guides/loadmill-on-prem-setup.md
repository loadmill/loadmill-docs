# Loadmill On-Prem Setup

This guide explains the basic requirements and setup for running Loadmill on-prem with Docker.

## Requirements

- A Linux machine that can run three containers on the same Docker network.
AWS EC2 t3.medium-t3.large or equivalent
(2 vCPUs, 4/8 GB RAM)
- Docker and Docker Compose installed.
- Port 8090 availble for use. If not available, you can change it in the Docker Compose file.
- Container images:
  - Redis **7+** (downloaded from the internet).
  - Postgres **15+** (downloaded from the internet).
  - Loadmill on-prem container image (provided by Loadmill upon request).

Once getting the Loadmill on-prem container image, load it into your Docker environment using:

```bash
docker load -i loadmill-on-prem.tar
```

## Architecture

Loadmill on-prem requires the following containers running on a shared Docker network ( the network is created automatically by Docker Compose):

- **Redis (7+)**
- **Postgres (15+)**
- **Loadmill on-prem**

![On-prem network topology](../assets/loadmill-on-prem-topology.png)

## Desktop Application

Users can also download the Loadmill desktop application and configure it to work with the on-prem server (not mandatory).

## AI Provider Configuration

Loadmill supports the following AI providers:

- OpenAI
- Azure OpenAI
- AWS Bedrock (using an OpenAI OSS model)
- Llama 3

You must have one of the providers running (hosted or SaaS) and supply the API token and base URL when running the Loadmill app.

## Running with Docker Compose

Before running the stack, create the Postgres data directory on the host:

```bash
sudo mkdir -p /var/lib/postgresql16/data
```
Add your Docker Compose configurations here:

### 1) Basic example (Using OpenAI)


Save the following to `docker-compose-on-prem.yml`, then run:

```bash
docker compose -f docker-compose-on-prem.yml up
```

```yaml
version: "3.9"
networks:
  loadmill-net:
    name: loadmill-net
    driver: bridge

services:
  redis:
    image: redis:7.2.5
    ports:
      - "6379:6379"
    container_name: loadmill-redis
    networks:
      - loadmill-net
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 5s
      timeout: 3s
      retries: 20

  postgres:
    image: postgres:16.2
    ports:
      - "5432:5432"
    container_name: loadmill-postgres
    networks:
      - loadmill-net
    environment:
      POSTGRES_PASSWORD: "<your_password>"
      POSTGRES_DB: "loadmill_db"
    volumes: 
      - /private/var/lib/postgresql16/data:/var/lib/postgresql16/data:z
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres -d loadmill_db"]
      interval: 5s
      timeout: 3s
      retries: 20

  loadmill-app:
    image: loadmill-on-prem:latest
    container_name: loadmill-app
    ports:
      - "8090:8090"
    networks:
      - loadmill-net
    environment:
      REDIS_URL: redis://redis:6379
      DATABASE_URL: postgresql://postgres:<your_password>@postgres:5432/loadmill_db
      GK_SYNC_INTERVAL: 99999999 
      OPENAI_API_KEY: <your_openai_key>

    depends_on:
      redis:
        condition: service_healthy
      postgres:
        condition: service_healthy
```

### 2) Using Azure OpenAI

```yaml
version: "3.9"
networks:
  loadmill-net:
    name: loadmill-net
    driver: bridge

services:
  redis:
    image: redis:7.2.5
    ports:
      - "6379:6379"
    container_name: loadmill-redis
    networks:
      - loadmill-net
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 5s
      timeout: 3s
      retries: 20

  postgres:
    image: postgres:16.2
    ports:
      - "5432:5432"
    container_name: loadmill-postgres
    networks:
      - loadmill-net
    environment:
      POSTGRES_PASSWORD: "<your_password>"  # make sure to change this password
      POSTGRES_DB: "loadmill_db"
    volumes: # Important - make sure /var/lib/postgresql16/data exists on host!
      - /private/var/lib/postgresql16/data:/var/lib/postgresql16/data:z
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres -d loadmill_db"]
      interval: 5s
      timeout: 3s
      retries: 20

  loadmill-app:
    image: loadmill-on-prem:latest
    container_name: loadmill-app
    ports:
      - "8090:8090"
    networks:
      - loadmill-net
    environment:
      REDIS_URL: redis://redis:6379
      DATABASE_URL: postgresql://postgres:<your_password>@postgres:5432/loadmill_db
      GK_SYNC_INTERVAL: 99999999
      OPENAI_BASE_URL: https://loadmill.openai.azure.com/openai/deployments/gpt-5.2 # an example
      AZURE_OPENAI_API_VERSION: <your_API_version>
      OPENAI_API_KEY: <your_azure_openai_key>


    depends_on:
      redis:
        condition: service_healthy
      postgres:
        condition: service_healthy

```

### 3) Using Llama

```yaml
version: "3.9"
networks:
  loadmill-net:
    name: loadmill-net
    driver: bridge

services:
  redis:
    image: redis:7.2.5
    ports:
      - "6379:6379"
    container_name: loadmill-redis
    networks:
      - loadmill-net
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 5s
      timeout: 3s
      retries: 20

  postgres:
    image: postgres:16.2
    ports:
      - "5432:5432"
    container_name: loadmill-postgres
    networks:
      - loadmill-net
    environment:
      POSTGRES_PASSWORD: "<your_password>"  # make sure to change this password
      POSTGRES_DB: "loadmill_db"
    volumes: # Important - make sure /var/lib/postgresql16/data exists on host!
      - /private/var/lib/postgresql16/data:/var/lib/postgresql16/data:z
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres -d loadmill_db"]
      interval: 5s
      timeout: 3s
      retries: 20

  loadmill-app:
    image: loadmill-on-prem:latest
    container_name: loadmill-app
    ports:
      - "8090:8090"
    networks:
      - loadmill-net
    environment:
      REDIS_URL: redis://redis:6379
      DATABASE_URL: postgresql://postgres:<your_password>@postgres:5432/loadmill_db
      GK_SYNC_INTERVAL: 99999999
      SELF_HOSTED_LLM_URL: <ollama_url>
      SELF_HOSTED_LLM_MODEL: llama3 # an example specify your model here

    depends_on:
      redis:
        condition: service_healthy
      postgres:
        condition: service_healthy

```
