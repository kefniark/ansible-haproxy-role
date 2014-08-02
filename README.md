ansible-haproxy-role
====================
[![Build Status](https://travis-ci.org/kefniark/ansible-haproxy-role.svg?branch=master)](https://travis-ci.org/kefniark/ansible-haproxy-role)

Install and configure haproxy under :
 - CentOS 6
 - Debian wheezy
 - Ubuntu 14
 
This repository is based on a MIT License

Documentation:
-------------------------

You can see [the documentation](https://github.com/kefniark/ansible-haproxy-role/blob/master/docs/main.yml) to see all available options.

There is also two configuration file :
 - A reverse proxy for a preinstalled webserver : [Exemple 1](https://github.com/kefniark/ansible-haproxy-role/blob/master/docs/exemple-simple-server.yml)
 - A loadbalancer in front of : [Exemple 2](https://github.com/kefniark/ansible-haproxy-role/blob/master/docs/exemple-loadbalancer.yml)

Example Playbook
-------------------------

```yaml
- hosts: all
  remote_user: root
  roles:
   - role: haproxy
     haproxy_frontends:
     - name: loadbalancer
       bind: '*:8080'
       default_backend: webserver
     haproxy_backends:
     - name: webserver
       servers:
        - name: backend1
          ip: localhost
          port: 80
```

More Informations
-------------------------
This project is still in development and lot options are missing or not fully tested.
You can follow the developpment status on : https://trello.com/b/TPJFH9rF/ansible-haproxy
