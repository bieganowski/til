Under linux to export all environment variables form the `.env` file, e.g.:
```text
PROJECT_ENVIRONMENT=local
DB_NAME=<...>
DB_USER=<...>
DB_PASSWORD=<...>
DB_HOST=localhost
DB_PORT=5432
```

One can use the following bash command:
```bash
set -o allexport; source .env; set +o allexport
```