# [Ansible role postgresql_replication](#postgresql_replication)

Ansible role to deploy postgresql software with replication

|GitHub|Version|Issues|Pull Requests|
|------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-postgresql_replication/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-postgresql_replication/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-postgresql_replication.svg)](https://github.com/buluma/ansible-role-postgresql_replication/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-postgresql_replication.svg)](https://github.com/buluma/ansible-role-postgresql_replication/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-postgresql_replication.svg)](https://github.com/buluma/ansible-role-postgresql_replication/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.postgresql_replication
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    # - role: buluma.postgresql
    - role: enix.postgresql
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/defaults/main.yml):

```yaml
---
# defaults file for postgresql_replication

postgresql_replication__group: "postgresql"
postgresql_replication__group_master: "postgresql_master"
postgresql_replication__group_replicas: "postgresql_replicas"

postgresql_replication__user: "replicate"
postgresql_replication__password: "replicate"

postgresql_replication__waldir: "/var/lib/postgresql/wal-slave/"
postgresql_replication__walsenders: 3
postgresql_replication__walsegments: 64

# !!! set this to 'yesiwant' to bootstrap cluster
# postgresql_replication__bootstrap undefined

postgresql_replication__trigger_file: "/tmp/MasterNow"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[enix.postgresql](https://galaxy.ansible.com/buluma/enix.postgresql)|[![Ansible Molecule](https://github.com/buluma/enix.postgresql/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/enix.postgresql/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/enix.postgresql.svg)](https://github.com/shadowwalker/enix.postgresql)|

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- enix.postgresql

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-postgresql_replication/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|

The minimum version of Ansible required is 2.1, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-postgresql_replication/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-postgresql_replication/blob/master/LICENSE).

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)


### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
