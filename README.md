Rundeck
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rundeck.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rundeck)

Provides Rundeck for your system.

Context
-------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/rundeck.png "Dependency")

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

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.6|yes|yes|yes|
|alpine-3.7|yes|yes|yes|
|archlinux|yes|yes|yes|
|centos-6|yes|yes|yes|
|centos-7|yes|yes|yes|
|debian-buster|yes|yes|yes|
|debian-stretch|yes|yes|yes|
|debian-wheezy|yes|yes|yes|
|debian-jessie|no|no|no|
|fedora-26|yes|yes|yes|
|fedora-27|yes|yes|yes|
|opensuse-42.2|yes|yes|yes|
|opensuse-42.3|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|
|ubunut-bionic|yes|yes|yes|

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
