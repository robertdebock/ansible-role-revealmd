Role Name
=========

Have revealmd available.

Requirements
------------

The package manager from nodejs (NPM) should be installed. robertdebock.npm can be used for that.

Role Variables
--------------

The variable directory can be set to something else than the default "/data".

```
---
- hosts: servers
  become: yes
  roles:
    - { role: revealmd, directory: /other/directory }
```

Dependencies
------------

The nodejs NPM package manager must be available, this roll can help:
- robertdebock.npm

Example Playbook
----------------

```
---
- hosts: servers
  become: yes
  roles:
    - revealmd
```

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
