# TodoApp — Dockerized Django + MySQL (DevOps case)

**Short description**  
Portfolio DevOps project demonstrating containerization of a Django REST API application with MySQL database using Docker and Docker Compose. Focuses on environment externalization, database integration, container orchestration (local), and automated migrations.

---

## Key highlights / stack
- Django REST API (sample application)  
- MySQL database container  
- Docker multi-stage build (app, DB)  
- Docker Compose orchestration (local)  
- Environment configuration via `.env`  
- Automated database migrations on startup  

---

## Repository structure (high-level)
```
.
├── docker-compose.yml       # Orchestration (app + DB)
├── Dockerfile               # Django app container
├── Dockerfile.mysql         # MySQL container with env config
├── .env.example             # Example environment variables
├── requirements.txt         # Python dependencies
├── manage.py                # Django management script
├── accounts/                # App code (not DevOps focus)
├── api/                     # App code (not DevOps focus)
├── lists/                   # App code (not DevOps focus)
└── todolist/                # App code (not DevOps focus)
```

---

## How it works
1. **Docker Compose** orchestrates two services:
   - `pythonapp` — Django application  
   - `mysql` — MySQL DB with persistent volume  
2. Environment variables are externalized in `.env`.  
3. On startup, the Django container:
   - installs dependencies,  
   - runs migrations automatically,  
   - starts the dev server on port `8080`.  
4. Application becomes available at [http://localhost:8080](http://localhost:8080).  

---

## Run locally

1. Copy the environment file:
   ```bash
   cp .env.example .env
   ```

2. Build and start containers:
   ```bash
   docker compose up --build
   ```

3. Access the application:
   ```
   http://localhost:8080
   ```

---

## Features
- Clear separation of services (Django app + MySQL DB)  
- Configurable via `.env` file  
- Persistent DB volume (`todoapp-db-data`)  
- Reusable multi-stage Dockerfiles  
- Automated Django DB migrations  

---

## Next steps / improvements
- Push Docker images to Docker Hub  
- Add GitHub Actions pipeline for CI/CD (lint, build, push)  
- Extend Docker Compose for production-like setup:
  - nginx reverse proxy  
  - gunicorn app server  
  - health checks  
- Add monitoring/logging stack (Prometheus/Grafana, ELK)  

---

## Contacts / Author
Project prepared as **portfolio DevOps case**, demonstrating Dockerization, Compose orchestration, environment externalization, and containerized DB integration.
