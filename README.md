Role Name
=========

Have revealmd available.

Requirements
------------

The package manager from nodejs (NPM) should be installed. robertdebock.npm can be used for that.

Role Variables
--------------

None known.

Dependencies
------------

robertdebock.npm

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
