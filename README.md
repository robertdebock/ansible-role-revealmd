revealmd
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-revealmd.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-revealmd)

Have revealmd available on your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/revealmd.png "Dependency")

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

- robertdebock.bootstrap
- robertdebock.epel
- robertdebock.npm

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.6|yes|yes|yes|
|alpine-3.7|yes|yes|yes|
|archlinux|yes|yes|yes|
|centos-6|no|no|no|
|centos-7|yes|yes|yes|
|debian-buster|no|no|no|
|debian-stretch|no|no|no|
|fedora-27|yes|yes|yes|
|fedora-28|yes|yes|yes|
|opensuse-42.2|yes|yes|yes|
|opensuse-42.3|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|
|ubuntu-bionic|yes|yes|yes|

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

Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
