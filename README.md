# fielddock-backend

Django backend and REST API for the FieldDock platform.

Official project website: https://fielddock.org

## What This Repository Contains

- Django backend service (`backend/`)
- API apps:
  - `missions/`
  - `devices/`
  - `services/`
- Admin/UI apps:
  - `admin_site/`
  - `admin_login/`
- Docker setup for development and production

## Tech Stack

- Python 3 + Django 4.2
- Django REST Framework
- MySQL (Docker profile)
- MQTT broker (Eclipse Mosquitto)
- OpenAPI docs support (`drf-spectacular` dependency)

## API and Routes

Base URL patterns from `backend/urls.py`:

- `/admin/` Django admin
- `/admin_site/` custom admin site routes
- `/` login/admin frontend routes (`admin_login`)
- `/api/` API endpoints from `missions`, `devices`, and `services`

## Local Development (No Docker)

1. Create and activate virtual env

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Use local settings

```bash
export DJANGO_SETTINGS_MODULE=backend.settings.local
```

4. Run migrations and server

```bash
python manage.py migrate
python manage.py runserver
```

## Docker Development

Uses `docker-compose.yml` with:
- app (`backend.settings.docker`)
- MySQL (`mysqldb`)
- MQTT (`mqtt`)

Start:

```bash
docker compose up --build
```

The app is available at `http://localhost:8000`.

## Production Compose

`docker-compose.prod.yml` expects a `.env` file for app secrets and DB values.

Minimum variables used by `backend.settings.prod`:

- `SECRET_KEY`
- `DATABASE_NAME`
- `DATABASE_USERNAME`
- `DATABASE_PASSWORD`
- `DATABASE_HOST`

Run:

```bash
docker compose -f docker-compose.prod.yml up -d --build
```

## Settings Profiles

- `backend.settings.local`: local SQLite dev
- `backend.settings.docker`: dockerized MySQL dev
- `backend.settings.prod`: production MySQL with env vars

## Repository Reference / Citation

If you reference or build on this backend, cite FieldDock:

- FieldDock project website: https://fielddock.org

Also see [`docs/CITATION.md`](docs/CITATION.md).
