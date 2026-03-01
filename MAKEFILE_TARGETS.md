# Makefile Targets Documentation

This document explains all available `make` targets in this repository.

## Prerequisites
- Docker Desktop is running.
- `docker compose` is installed.
- `.env` exists (recommended):
  ```bash
  cp .env.example .env
  ```

## Variables Used by Targets
- `service`: required by `logs` and `shell`.
- `shell_cmd`: optional for `shell` (default: `/bin/bash`).
- `NAME`: required by `scaffold-app`.
- `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`: required by `sql` (loaded from `.env`).

## Lifecycle Targets

### `make up`
Start all services in detached mode.

### `make down`
Stop all services.

### `make restart`
Stop and restart with rebuild (`docker compose up -d --build`).

### `make build`
Build service images.

## Monitoring Targets

### `make status`
Show running containers (`docker compose ps`).

### `make logs service=<name>`
Tail logs for one service.

Examples:
```bash
make logs service=backend
make logs service=frontend
make logs service=db
```

## Cleanup Targets

### `make clean`
Stop containers and remove orphans.

### `make fclean`
Stop containers and remove volumes + images + orphans.

### `make clean-reset`
Dangerous reset:
- stops containers
- deletes `./db-data`
- removes Python `__pycache__` folders

### `make reset`
Runs `fclean` then `clean-reset`.

## Backend / Django Targets

### `make migrations`
Create Django migrations.

### `make migrate`
Apply Django migrations.

### `make test`
Run Django tests.

### `make superuser`
Create Django superuser interactively.

## Access / Shell Targets

### `make shell service=<name> [shell_cmd=<cmd>]`
Run custom shell command in a service.

Examples:
```bash
make shell service=backend
make shell service=frontend shell_cmd=sh
make shell service=db
```

### `make sql`
Open `psql` in db container using env credentials.

## Scaffolding Targets

### `make scaffold-project`
Create Django project (`core`) in backend workspace.

### `make scaffold-app NAME=<app_name>`
Create a new Django app.

Example:
```bash
make scaffold-app NAME=plots
```

### `make scaffold-frontend`
Run interactive Vite scaffolding in frontend container.

## Notes / Caveats
- `init` is listed in `.PHONY` but no `init:` target exists currently.
- `clean-reset` uses `sudo rm -rf ./db-data`; use carefully.
- Run `make up` before targets that use `docker compose exec`.
