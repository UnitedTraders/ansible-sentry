Role Name
=========

Role for installing dockerized Sentry (<https://getsentry.com/welcome/>)

Requirements
------------

Any host with docker, docker-compose and systemd should be work.

Role Variables
--------------

* `sentry_secret_key` - **required**. Secret hash for Sentry, must be at least 32 characters long.
* `sentry_home` - default `/opt/sentry`. Directory for Sentry data and docker-compose files.
* `sentry_user` - default 'sentry'. Owner of `sentry_home`.
* `sentry_db_user` - default 'sentry'. PostgreSQL user for Sentry database.
* `sentry_db_password` - default 'sentry'. PostgreSQL pasword for Sentry database user.
* `sentry_web_port` - default '9000'. HTTP port for mapping Sentry web container.
* `sentry_admins` - list of Sentry superadmins. Example:
```
sentry_admins:
  - email: "admin@{{ inventory_hostname }}"
    password: "admin"
```

Example Playbook
----------------
```
- hosts: sentry
  name: sentry
  roles:
    - role: ansible-docker
      docker_compose_version: '1.8'
      docker_api_version: '1.9'
    - role: unitedtraders.sentry
```

License
-------

BSD

Author Information
------------------

Anton Markelov <doublic@gmail.com> - <https://github.com/strangeman>
