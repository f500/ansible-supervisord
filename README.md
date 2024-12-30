supervisord
========

Basic Supervisord install

Requirements
------------

None

Role Variables
--------------

    supervisord_unix_http_server_socket_file:   "/var/run/supervisor.sock"
    supervisord_unix_http_server_socket_mode:   "0700"
    supervisord_unix_http_server_socket_chown:  "root:supervisord"
    
    supervisord_logfile:      "/var/log/supervisor/supervisord.log"
    supervisord_pidfile:      "/var/run/supervisord.pid"
    supervisord_childlogdir:  "/var/log/supervisor"
    
    supervisord_supervisorctl_serverurl:  "unix://{{ supervisord_unix_http_server_socket_file }}"
    
    supervisord_include_path: "/etc/supervisor/conf.d"
    supervisord_include_files: "{{ supervisord_include_path }}/*.conf"


Example Playbook
-------------------------

    - hosts: servers
      roles:
         - { role: f500.supervisord }

Linting
-------
Github actions will check this role with ansible-lint. To run this locally, you will need to follow the following steps:

```bash
brew install ansible-lint
brew install yamllint
ansible-lint
```

to fix the linting errors, run:

```bash
ansible-lint --fix
```

License
-------

LGPL

Author Information
------------------

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl
