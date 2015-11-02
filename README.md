nomad
=====

[![Ansible Role](https://img.shields.io/ansible/role/5300.svg)](https://galaxy.ansible.com/list#/roles/5300)

Installs Nomad

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name            | Default                                                          | Description                 |
|-----------------|------------------------------------------------------------------|-----------------------------|
| nomad_version   | 0.1.2                                                            | Version of Nomad to install |
| nomad_sha256sum | 3335f7acb0d5eacaaa19aea37d128418ace18e6ef03d38de0c2c52ce831d7934 | SHA 256 checksum of package |

Dependencies
------------

- kbrebanov.unzip

Example Playbook
----------------

Install Nomad
```
- hosts: all
  roles:
    - { role: kbrebanov.nomad }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
