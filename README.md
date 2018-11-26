rundeck
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rundeck.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rundeck)

The purpose of this role is to install and configure rundeck on your system.

Example Playbook
----------------

This example is taken from `molecule/default/playbook.yml`:
```
---
- name: Converge
  hosts: all
  gather_facts: false
  become: true

  roles:
    - robertdebock.bootstrap
    - robertdebock.java
    - robertdebock.rundeck

```

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```
---
# defaults file for rundeck

# Where to install rundeck.
rundeck_rdeckbase: /opt/rundeck

# The Xmx memory size in mb. (Stored in: "{{ rundeck_rdeckbase }}/etc/profile".)
rundeck_xmx: 1024
rundeck_xms: 256
rundeck_maxmetaspacesize: 128

# The URL where Rundeck will be served on:
rundeck_port: 4440
rundeck_address: "127.0.0.1"
rundeck_server_web_context: /

rundeck_url: "http://{{ rundeck_address }}:{{ rundeck_port }}{{ rundeck_server_web_context }}"

rundeck_config:
  - parameter: grails.serverURL
    value: "{{ rundeck_url }}"

# The settings for Rundeck. (Stored in: "{{ rundeck_rdeckbase }}/etc/framework.properties".)
rundeck_framework:
  - parameter: framework.server.hostname
    value: "{{ ansible_fqdn }}"
  - parameter: framework.server.name
    value: "{{ ansible_fqdn }}"
  - parameter: framework.projects.dir
    value: "{{ rundeck_rdeckbase }}/projects"
  - parameter: framework.var.dir
    value: "{{ rundeck_rdeckbase }}/var"
  - parameter: framework.logs.dir
    value: "{{ rundeck_rdeckbase }}/var/logs"
  # - parameter: "framework.server.username"
  #   value: unset
  # - parameter: "framework.server.password"
  #   value: unset
  - parameter: framework.rundeck.url
    value: "{{ rundeck_url }}"
  # - parameter: "framework.ssh.keypath"
  #   value: unset
  # - parameter: "framework.ssh.user"
  #   value: unset
  - parameter: framework.ssh-connect-timeout
    value: 0
  - parameter: framework.ssh-command-timeout
    value: 0
  # - parameter: "framework.log.dispatch.console.format"
  #   value: unset
  - parameter: framework.rundeck.execution.script.tokenexpansion.enabled
    value: true

# Some Docker containers do not allow managing services, rebooting and writing
# to some locations in /etc. The role skips tasks that will typically fail in
# Docker. With this parameter you can tell the role to -not- skip these tasks.
rundeck_ignore_docker: yes

```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

---
- robertdebock.bootstrap
- robertdebock.java


Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/rundeck.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes*|
|alpine-latest|yes|yes|yes*|
|archlinux|yes|yes|yes*|
|centos-6|yes|yes|yes*|
|centos-latest|yes|yes|yes*|
|debian-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes*|
|opensuse-leap|yes|yes|yes*|
|opensuse-tumbleweed|yes|yes|yes*|
|ubuntu-artful|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-rundeck) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-rundeck/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

Run the [ansible-galaxy](https://github.com/ansible/galaxy-lint-rules) and [my](https://github.com/robertdebock/ansible-lint-rules) lint rules if you want your change to be merges:
```
ansible-lint -r /path/to/galaxy-lint-rules/rules .
ansible-lint -r /path/to/ansible-lint-rules/rules .
```

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
