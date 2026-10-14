# postgres

ставлю постгру и делаю свой кластер в postgres__data_dir, + конфиги, службы, базы, пользователей и postgres_exporter.

## Переменные

```yaml
postgres__data_dir: /data/postgres/data
postgres__port: 5434
postgres__service_name: postgres-custom

# параметры postgresql.conf
postgres__opts:
  max_connections: 100
  shared_buffers: 128MB

# правила pg_hba конфига
postgres__hba:
  - { type: local, database: all, user: all, method: peer }
  - { type: host, database: all, user: all, address: 127.0.0.1/32, method: scram-sha-256 }

postgres__users: []       # [{name, password, attrs}]
postgres__databases: []   # [{name, owner}]

postgres__exporter_version: "0.20.1"
postgres__exporter_port: 9187
postgres__exporter_user: postgres_exporter
postgres__exporter_password: ""   # из vault
```

## Пример

```yaml
- hosts: vm1
  roles:
    - role: postgres
      vars:
        postgres__users:
          - name: app
            password: "{{ vault_postgres_app_password }}"
        postgres__databases:
          - name: appdb
            owner: app
        postgres__exporter_password: "{{ vault_postgres_exporter_password }}"
```
