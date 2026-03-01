# Django + PostGIS + React DevOps Template

Docker-based DevOps template for:
- PostgreSQL + PostGIS
- Django backend service
- React (Vite) frontend service
- Makefile workflow for common tasks

## Included
- `docker-compose.yml`
- `Makefile`
- `backend/Dockerfile`
- `backend/entrypoint.sh`
- `backend/requirements.txt`
- `frontend/Dockerfile`
- `frontend/entrypoint.sh`
- `.env.example`

## Environment
Create `.env` from template:

```bash
cp .env.example .env
```

Example values (already in `.env.example`):

```env
POSTGRES_DB=app_db
POSTGRES_USER=app_user
POSTGRES_PASSWORD=app_password
DB_HOST=db
DB_PORT=5432

VITE_API_URL=http://localhost:8000
VITE_MAPBOX_TOKEN=your_token_here
```

## Quick Start
```bash
make up
make status
```

## Useful Commands
```bash
make logs service=backend
make logs service=frontend
make shell service=backend
make shell service=frontend shell_cmd=sh
make shell service=db
make down
```

## Ports
- Backend: `8000`
- Frontend: `5173`
- Postgres/PostGIS: `25432` (mapped to container `5432`)

## DB Tools (DBeaver / CLI)
Use:
- Host: `localhost`
- Port: `25432`
- Database/User/Password: from `.env`

## Notes
- This repository is DevOps/infrastructure template only.
- Add your project source code under `backend/` and `frontend/`.
- `kartoza/postgis:16-3.4` supports `linux/amd64` and `linux/arm64`.
