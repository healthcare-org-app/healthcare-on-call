# on-call-service

on-call-service — domain: providers

- **Port:** 8205
- **Language:** Python 3.11 + Flask
- **Database:** `providers` (Postgres, table `on_call`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/on_call/`          |
| POST      | `/api/on_call/`          |
| GET       | `/api/on_call/<id>`      |
| PUT/PATCH | `/api/on_call/<id>`      |
| DELETE    | `/api/on_call/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** (none)
**Subscribes:** (none)

## HTTP peer dependencies

- `providers-service`
- `provider-schedule-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
