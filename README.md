Rundeck
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rundeck.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rundeck)

Provides Rundeck for your system.

Context
-------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/rundeck.png "Dependency")

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

- [robertdebock.bootstrap](https://travis-ci.org/robertdebock/ansible-role-bootstrap)
- [robertdebock.java](https://travis-ci.org/robertdebock/ansible-role-java)

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

These dependencies are not listed in meta/main.yml, because this would run the role with default values, which may lead the installation of a java version or type that does not match your desired situation.

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-latest|yes|yes|yes|
|alpine-edge|yes|yes|yes|
|archlinux|yes|yes|yes|
|centos-6|yes|yes|yes|
|centos-latest|yes|yes|yes|
|debian-stable|yes|yes|yes|
|debian-latest|yes|yes|yes|
|debian-wheezy|yes|yes|yes|
|fedora-latest|yes|yes|yes|
|fedora-rawhide|yes|yes|yes|
|opensuse-leap|yes|yes|yes|
|opensuse-tumbleweed|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|
|ubunut-bionic|yes|yes|yes|

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.java
    - role: robertdebock.rundeck

```

Install this role using `galaxy install robertdebock.rundeck`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
