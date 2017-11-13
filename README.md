revealmd
=========

Have revealmd available on your system.

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

directory - the location where revealmd will look for .md files, defaults to /data.
options - the extra options that you'd want revealmd to start with, defaults to none.
port - the TCP to listen to, defaults to 1948.

Dependencies
------------

- robertdebock.npm

Example Playbook
----------------

```
```
---
- hosts: servers
  become: yes

  roles:
    - role: revealmd
      directory: /other/directory
      options: theme: solarized

  tasks:
    - name: place content
      copy:
        src: files/index.md
        dest: /other/directory/index.md
```

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
