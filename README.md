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