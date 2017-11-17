Ansible role to create docker container with Postgres

### Requirements

Tested on:
* Ubuntu 16.04
* Ansible 2.5.0
* Python 2.7.12
* Docker API 1.29
* docker-py 1.10.6

Expected requirements:
* Ubuntu/Debian any version
* python >= 2.6
* docker-py >= 1.7.0
* Docker API >= 1.20

### Configurable parameters and defaults
```
postgres_docker_image: postgres
postgres_docker_image_tag: 1.6
postgres_container_name: postgres
postgres_port: 5432

postgres_service_name: postgresql
postgres_uid: 19192

postgres_path_postfix: "{{ postgres_service_name.startswith('postgres') | ternary('','postgres-') }}{{ postgres_service_name }}"
postgres_data_dir: "/data/{{postgres_path_postfix}}"
postgres_logs_dir: "/var/log/{{postgres_path_postfix}}"

postgres_memory_mb: 4096
postgres_memory_swap: "{{postgres_memory_mb}}"
postgres_cpu_shares: 512

postgres_user: postgres
postgres_password: 12345678
postgres_database: default
```

### Example Playbook

`pg.yml`
```
- hosts: database
  roles:
  - role: ansible-docker-postgres
```

Create and Postgres service with:
`sudo ansible-playbook pg.yml`

Stop and remove Postgres service with:
`sudo ansible-playbook pg.yml --extra-vars "uninstall=true"`