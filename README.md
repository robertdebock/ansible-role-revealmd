revealmd
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
    - { role: revealmd, directory: /other/directory, options: theme: solarized }
```

Dependencies
------------

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
