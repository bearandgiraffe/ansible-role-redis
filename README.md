nginx
=========

Installs and configures nginx.

Requirements
------------

None.

Role Variables
--------------

```yml
redis_port:           6379
redis_bind_interface: 127.0.0.1
redis_unixsocket:     ''
redis_timeout:        300

redis_daemon:     redis-server
redis_conf_path:  /etc/redis/redis.conf

redis_loglevel: "notice"
redis_logfile:  /var/log/redis/redis-server.log

redis_databases: 16

# Set to an empty set to disable persistence (saving the DB to disk).
redis_save:
  - 900 1
  - 300 10
  - 60 10000

redis_rdbcompression: "yes"
redis_dbfilename:     dump.rdb
redis_dbdir:          /var/lib/redis

redis_maxmemory:          0
redis_maxmemory_policy:   "noeviction"
redis_maxmemory_samples:  5

redis_appendonly:   "no"
redis_appendfsync:  "everysec"

# Add extra include files for local configuration/overrides.
redis_includes: []

```

Dependencies
------------

```
bearandgiraffe.base
```

Example Playbook
----------------

```yml
- hosts: servers
  roles:
    - { role: bearandgiraffe.redis, redis_port: '6379' }
```

License
-------

The Unlicense (see LICENSE)

Author Information
------------------

Youssef Chaker (@ychaker) from Bear & Giraffe LLC (@bearandgiraffe).
