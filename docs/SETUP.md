# Setup Notes

## Prerequisites

- Python 3.10+ recommended
- pip
- Docker + Docker Compose (for container workflow)

## Local Quick Commands

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export DJANGO_SETTINGS_MODULE=backend.settings.local
python manage.py migrate
python manage.py runserver
```

## Docker Quick Commands

```bash
docker compose up --build
```

## Useful Django Commands

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py test
```
