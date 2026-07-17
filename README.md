# MERN DevOps Task Manager 

A professional MERN stack task management application with Docker, CI/CD readiness, JWT authentication, and health checks.

## Overview

This project is a task manager built with React, Node.js, Express, and MongoDB. It includes a Docker Compose setup, Nginx reverse proxy support, security middleware, JWT auth, and a CI/CD-ready Jenkins pipeline.

## Features

- User registration and login
- JWT authentication and protected API routes
- Task creation, update, delete, and list
- React frontend with dashboard and modals
- Dockerized backend and frontend
- Health checks for MongoDB, backend, and frontend
- Security middleware: Helmet, rate limiting, CORS
- CI/CD-ready Jenkinsfile structure

## Tech Stack

- Frontend: React 18, React Router v6, Axios
- Backend: Node.js, Express.js, Mongoose
- Database: MongoDB / MongoDB Atlas
- Auth: JWT, bcryptjs
- Reverse Proxy: Nginx
- Containers: Docker, Docker Compose
- CI/CD: Jenkins

## Folder Structure

```text
├── backend/                    # Node + Express API
│   ├── middleware/             # JWT auth and security
│   ├── models/                 # User and Task schemas
│   ├── routes/                 # Auth, task, health endpoints
│   ├── server.js               # Backend entry point
│   └── Dockerfile
├── frontend/                   # React application served by Nginx
│   ├── src/                    # React source
│   ├── nginx/                  # Nginx configuration
│   └── Dockerfile
├── docker-compose.yml          # Local full-stack orchestration
├── Jenkinsfile                 # CI/CD pipeline definition
└── .gitignore                  # Ignored files
```

## Installation

### Prerequisites

- Node.js 18+
- npm
- Docker & Docker Compose
- MongoDB Atlas or local MongoDB

### Run Locally

```bash
cd backend
npm install
npm run dev
```

```bash
cd frontend
npm install
npm start
```

Open app at `http://localhost:3000`.

## Environment Variables

Create `backend/.env` with:

```env
NODE_ENV=development
PORT=5001
MONGO_URI=mongodb://user:pass@host:27017/dbname?authSource=admin
JWT_SECRET=your_strong_secret_here
JWT_EXPIRE=7d
CLIENT_URL=http://localhost:3000
```

## Running the App

### Backend

```bash
cd backend
npm run dev
```

### Frontend

```bash
cd frontend
npm start
```

## Docker Usage

```bash
docker compose up --build
```

- Frontend: `http://localhost`
- Backend API container: `http://localhost:5000`
- Health: `http://localhost:5000/health`

## API Endpoints

### Auth

| Method | Endpoint               | Auth | Description        |
|--------|------------------------|------|--------------------|
| POST   | `/api/auth/register`   | ❌   | Register a user    |
| POST   | `/api/auth/login`      | ❌   | Login and return JWT |
| GET    | `/api/auth/me`         | ✅   | Get current user   |

### Tasks

| Method | Endpoint               | Auth | Description         |
|--------|------------------------|------|---------------------|
| GET    | `/api/tasks`           | ✅   | List tasks          |
| POST   | `/api/tasks`           | ✅   | Create task         |
| PUT    | `/api/tasks/:id`       | ✅   | Update task         |
| DELETE | `/api/tasks/:id`       | ✅   | Delete task         |

### Health

| Method | Endpoint   | Auth | Description                |
|--------|------------|------|----------------------------|
| GET    | `/health`  | ❌   | Service health check       |

## DevOps Practices

- Containerized backend and frontend
- Docker Compose orchestration
- Nginx reverse proxy for React SPA and API
- Health checks for MongoDB, backend, frontend
- Helmet, rate limiting, CORS security middleware
- JWT auth with protected routes
- Environment variable configuration
- Jenkins CI/CD-ready structure

## Future Improvements

- Add frontend unit and E2E tests
- Add GitHub Actions workflow for PR validation
- Add HTTPS / TLS automation
- Add centralized logging and monitoring
- Add staging and production deployment branches

## Screenshots

- `screenshots/login.png`
- `screenshots/dashboard.png`
- `screenshots/task-create.png`
