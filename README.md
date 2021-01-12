# [revealmd](#revealmd)

Install and configure revealmd on your system.

|Travis|GitHub|GitLab|Quality|Downloads|Version|
|------|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-revealmd.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-revealmd)|[![github](https://github.com/robertdebock/ansible-role-revealmd/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-revealmd/actions)|[![gitlab](https://gitlab.com/robertdebock/ansible-role-revealmd/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-revealmd)|[![quality](https://img.shields.io/ansible/quality/21646)](https://galaxy.ansible.com/robertdebock/revealmd)|[![downloads](https://img.shields.io/ansible/role/d/21646)](https://galaxy.ansible.com/robertdebock/revealmd)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-revealmd.svg)](https://github.com/robertdebock/ansible-role-revealmd/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.revealmd
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.git
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for revealmd

# The directory where reveal-md should find presentations.
revealmd_directory: /data

# The exact presentation to process
revealmd_presentation: index.md

# The tcp port where reveal-md should listen on.
revealmd_port: 1948

# The theme to use.
# https://github.com/highlightjs/highlight.js/tree/master/src/styles
revealmd_options: --theme black
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-revealmd/blob/master/requirements.txt).

## [Status of requirements](#status-of-requirements)

The following roles are used to prepare a system. You may choose to prepare your system in another way, I have tested these roles as well.

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |
| [robertdebock.epel](https://galaxy.ansible.com/robertdebock/epel) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-epel.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-epel) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-epel/actions) |
| [robertdebock.git](https://galaxy.ansible.com/robertdebock/git) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-git.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-git) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-git/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-git/actions) |
| [robertdebock.npm](https://galaxy.ansible.com/robertdebock/npm) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-npm.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-npm) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-npm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-npm/actions) |
| [robertdebock.service](https://galaxy.ansible.com/robertdebock/service) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-service.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-service) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-service/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-service/actions) |

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- robertdebock.npm
## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/ansible-role-revealmd/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|el|8|
|debian|buster|
|fedora|all|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| centos:7 | /usr/lib/node_modules/reveal-md/bin/reveal-md.js:29 (async () => { |
| redhat:7 | /usr/lib/node_modules/reveal-md/bin/reveal-md.js:29 (async () => { |


## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-revealmd) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-revealmd/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
