revealmd
=========

[![Build Status](https://travis-ci.org/robertdebock.ansible-role-revealmd.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-revealmd)

Have revealmd available on your system.

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

directory - the location where revealmd will look for .md files, defaults to /data.
options - the extra options that you'd want revealmd to start with, defaults to none.
appport - the TCP to listen to, defaults to 1948.

Dependencies
------------

- robertdebock.npm
- robertdebock.git

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Example Playbook
----------------

```
---
- hosts: servers
  become: yes

  roles:
    - role: robertdebock.revealmd
      directory: /other/directory
      options: theme: solarized
      appport: 8080

  tasks:
    - name: place content
      copy:
        src: files/index.md
        dest: /other/directory/index.md
```

Install this role using `galaxy install robertdebock.revealmd`.


License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
