Ansible role to create docker container with Postgres

## Requirements

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

## Configurable parameters and defaults

See [defaults](defaults/main.yml)

## Example Playbook

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

## License

[Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)

This code was developed by me during my work in [SBDA Group](http://sbdagroup.com/)