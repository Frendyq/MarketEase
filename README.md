# MarketEase

Warehouse management system with role-based access and a REST API.

## Stack

- Backend: Go, Gin, Gorm, PostgreSQL, JWT, Swagger
- Frontend: Next.js, TypeScript, Tailwind CSS
- Deployment: Docker, Docker Compose

## Features

- Registration, login and token refresh (JWT)
- User profile and password change
- Three roles: viewer, manager, director
- Product management: create, update, soft delete and restore, stock and price per product
- User administration for the director role: assign roles, ban and unban, delete and restore users
- Swagger documentation at /swagger/index.html

## Access rules

- viewer: read products
- manager: viewer rights, plus create, update, delete and restore products
- director: manager rights, plus user administration

## Running

Create the configuration files from the examples and set your own values (use the same database password in both):

```bash
cp .env.example .env
cp backend/.env.example backend/.env
```

Then start everything:

```bash
docker-compose up --build
```

This starts PostgreSQL, the backend (port 8080) and the frontend (port 3000).

## Structure

```
backend/
  cmd/server/        entry point and Swagger docs
  config/            configuration
  internal/
    controllers/     HTTP handlers
    services/        business logic
    repositories/    database access
    models/          Gorm models
    middlewares/     authentication and role checks
    routes/          route table
    database/        connection and seed data
frontend/            Next.js app
docker-compose.yml
```
