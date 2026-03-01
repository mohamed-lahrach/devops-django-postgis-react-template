# Django + PostGIS + React DevOps Template

DevOps/infra template for a Dockerized stack:
- PostgreSQL + PostGIS
- Django backend container
- React (Vite) frontend container
- Makefile shortcuts

## Included Files
- `docker-compose.yml`
- `Makefile`
- `backend/Dockerfile`
- `backend/entrypoint.sh`
- `backend/requirements.txt`
- `frontend/Dockerfile`
- `frontend/entrypoint.sh`
- `.env.example`

## Quick Start
1. Copy env file:
   ```bash
   cp .env.example .env
   ```
2. Build and start:
   ```bash
   make up
   ```
3. Check services:
   ```bash
   make status
   ```

## Default Ports
- Backend API: `8000`
- Frontend dev server: `5173`
- PostgreSQL: `5432`

## Notes
- This template intentionally contains only DevOps/infrastructure files.
- Add your own Django app code under `backend/` and React app code under `frontend/`.
- Adjust image names, project naming, and service commands as needed for your project.
