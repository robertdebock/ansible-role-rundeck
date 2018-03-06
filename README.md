Rundeck
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rundeck.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rundeck)

Provides Rundeck for your system.

Requirements
------------

Access to a repository containing packages, likely on the internet.
A total memory (RAM) size exceeding the setting `rundeck_xmx`.
Have java available. Hint: robertdebock.java

Role Variables
--------------

See defaults/main for more details:

- rundeck_url
- rundeck_xmx
- rundeck_xms
- rundeck_maxmetaspacesize
- rundeck_rdeckbase

Dependencies
------------

You can include these roles to meet all requirements for this role.

- robertdebock.bootstrap
- robertdebock.java

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

These dependencies are not listed in meta/main.yml, because this would run the role with default values, which may lead the installation of a java version or type that does not match your desired situation.

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.java
      java_version: 8
    - robertdebock.rundeck

```

Install this role using `galaxy install robertdebock.rundeck`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
