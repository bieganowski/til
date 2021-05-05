## For Postgres on the host machine & app in container

Change Postgres configuration to allow external connections:
* pg_hba.conf -> add a row for docker0 address from `ip a` (or simply `0.0.0.0\0` to allow all access)
* postgresql.conf -> uncomment line and allow all, or just specific listen_addresses `listen_addresses = '*'`
