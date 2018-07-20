revealmd
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-revealmd.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-revealmd)

Have revealmd available on your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/revealmd.png "Dependency")

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- Have NPM installed.

Role Variables
--------------

revealmd_directory - the location where revealmd will look for .md files, defaults to /data.
revealmd_options - the extra options that you'd want revealmd to start with, defaults to none.
revealmd_port - the TCP to listen to, defaults to 1948.

Dependencies
------------

These implicit dependencies can help you get your system into the right state.

- [robertdebock.bootstrap](https://travis-ci.org/robertdebock/ansible-role-bootstrap)
- [robertdebock.epel](https://travis-ci.org/robertdebock/ansible-role-epel)
- [robertdebock.npm](https://travis-ci.org/robertdebock/ansible-role-npm)

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|
|------------|-----------|-----------|-----------|
|alpine-edge|yes|yes|yes|
|alpine-latest|yes|yes|yes|
|archlinux|yes|yes|yes|
|centos-6|no|no|no|
|centos-latest|yes|yes|yes|
|debian-latest|no|no|no|
|debian-stable|no|no|no|
|fedora-latest|yes|yes|yes|
|fedora-rawhide|no|no|no|
|opensuse-leap|yes|yes|yes|
|opensuse-tumbleweed|no|no|no|
|ubuntu-artful|yes|yes|yes|
|ubuntu-latest|yes|yes|yes|

Example Playbook
----------------

```
---
- hosts: servers
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.npm
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

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
