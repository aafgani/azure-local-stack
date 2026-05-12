# Local Dev Infra

Local development infrastructure stack powered by Docker Compose.

This repository provides containerized infrastructure services commonly used in backend and microservices development, including:

- SQL Server
- Azure Cosmos DB Emulator
- Azurite (Azure Storage Emulator)

The goal is to provide a reusable local development environment that is easy to start, maintain, and extend.

---

# Tech Stack

- Docker
- Docker Compose
- SQL Server 2019
- Azure Cosmos DB Emulator
- Azurite

---

# Services

| Service            | Port  | Description                  |
| ------------------ | ----- | ---------------------------- |
| SQL Server         | 1433  | Relational database          |
| Cosmos DB Emulator | 8081  | Local Cosmos DB emulator     |
| Azurite Blob       | 10000 | Azure Blob Storage emulator  |
| Azurite Queue      | 10001 | Azure Queue Storage emulator |
| Azurite Table      | 10002 | Azure Table Storage emulator |

---

# Getting Started

## Prerequisites

- Docker Desktop
- Docker Compose

Verify installation:

```bash
docker --version
docker compose version
```

---

# Start Services

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

Stop services:

```bash
docker compose down
```

---

# Project Structure

```text
.
├── compose.yaml
├── .env
├── sqlserver/
├── cosmosdb/
├── azurite/
└── docs/
```

---

# SQL Server

## Connection

```text
Server=127.0.0.1,1433;
Database=master;
User ID=sa;
Password=Password@123;
TrustServerCertificate=True;
```

## VS Code MSSQL Extension

Server:

```text
127.0.0.1,1433
```

Authentication:

```text
SQL Login
```

---

# Cosmos DB Emulator

## Endpoint

```text
https://localhost:8081/
```

## Default Emulator Key

```text
C2y6yDjf5/R+ob0N8A7Cgv30VRDj...
```

## Example Connection String

```text
AccountEndpoint=https://localhost:8081/;
AccountKey=C2y6yDjf5/R+ob0N8A7Cgv30VRDj...;
```

> Note:
> The Cosmos DB Emulator uses a self-signed certificate.
> You may need to trust the certificate locally.

---

# Azurite

## Blob Storage

```text
http://127.0.0.1:10000/devstoreaccount1
```

## Queue Storage

```text
http://127.0.0.1:10001/devstoreaccount1
```

## Table Storage

```text
http://127.0.0.1:10002/devstoreaccount1
```

## Default Storage Account

```text
AccountName=devstoreaccount1
AccountKey=Eby8vdM02xNOcqFe...
```

---

# Useful Commands

## View Logs

```bash
docker compose logs -f
```

Specific service:

```bash
docker compose logs -f sqlserver
```

---

# Persisted Data

Docker named volumes are used to persist local data between container restarts.

To remove all volumes:

```bash
docker compose down -v
```

---

# Future Plans

Potential future services:

- Redis
- RabbitMQ
- Seq
- HashiCorp Vault
- PostgreSQL
- MongoDB
- Keycloak

---

# Disclaimer

This repository is intended for local development and learning purposes only.

Do not use this setup in production environments.

---

# License

MIT
