# Notion API
# Event-Driven Microservices with Kafka & PostgreSQL

<p align="center">
  <img src="https://nodejs.org/static/images/logo.svg" width="120" />
  <img src="https://kafka.apache.org/images/apache-kafka.png" width="120" />
  <img src="https://www.postgresql.org/media/img/about/press/elephant.png" width="120" />
  <img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" width="120" />
</p>

A production-style microservices backend built with **TypeScript, PostgreSQL, Kafka, and Docker**.

This project demonstrates a real-world **event-driven architecture** using asynchronous communication between services.

---

# 🏗 Architecture Overview

```
Client
   ↓
API Gateway
   ↓
User Service ── Kafka (transaction_created) ──▶ Transaction Service
      │                                              │
      ▼                                              ▼
 Postgres (user-db)                           Postgres (transaction-db)
```

---

# 📦 Project Structure

```
.
├── api-gateway/
├── user-service/
├── note-service/
├── docker-compose.yml
└── README.md
```

### API Gateway
- Single entry point
- Routes client requests to internal services

### User Service
- Manages users
- Publishes `transaction_created` events to Kafka
- Owns its PostgreSQL database

### Transaction / Note Service
- Consumes Kafka events
- Processes and stores data
- Owns its own PostgreSQL database

---

# 🚀 Tech Stack

## Backend
- Node.js
- TypeScript
- Express.js

## Database
- PostgreSQL 15
- Prisma ORM

## Messaging
- Apache Kafka
- Zookeeper

## Infrastructure
- Docker
- Docker Compose

---

# 🔄 Event Flow

1. Client sends request to API Gateway.
2. Gateway forwards request to User Service.
3. User Service saves data to PostgreSQL.
4. User Service publishes event to Kafka.
5. Consumer service listens to Kafka topic.
6. Consumer service processes and persists data.

---

# ▶ Running the Project

Start all services:

```bash
docker-compose up --build
```

API Gateway:

```
http://localhost:4000
```

---

# 🧠 Why This Architecture

- Independent service scaling
- Loose coupling between services
- Reliable asynchronous communication
- Database per service pattern
- Production-ready structure

---

# 📈 Future Improvements

- JWT Authentication
- Outbox Pattern
- Dead Letter Queue
- Centralized Logging
- Monitoring (Prometheus + Grafana)
- Kubernetes Deployment
- CI/CD Integration

---

This repository serves as a foundational blueprint for building scalable, distributed backend systems.

```
note/
├── docker-compose.yml
│
├── api-gateway/
│   ├── src/index.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── Dockerfile
│
├── user-service/
│   ├── prisma/
│   │   └── schema.prisma
│   ├── src/
│   │   ├── index.ts
│   │   ├── kafka/producer.ts
│   │   └── repository/user.repository.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── Dockerfile
│
├── transaction-service/
│   ├── prisma/
│   │   └── schema.prisma
│   ├── src/
│   │   ├── index.ts
│   │   ├── kafka/consumer.ts
│   │   └── repository/transaction.repository.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── Dockerfile

```