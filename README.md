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
| nomad_version   | 0.2.0                                                            | Version of Nomad to install |
| nomad_sha256sum | f4525cbd99fd57ef607f9556be4f4bc39f82391947f40cc993538bba7da5bf90 | SHA 256 checksum of package |

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
