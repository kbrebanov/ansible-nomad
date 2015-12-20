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
| nomad_version   | 0.2.3                                                            | Version of Nomad to install |
| nomad_sha256sum | 0f3a7083d160893a291b5f8b4359683c2df7991fa0a3e969f8785ddb40332a8c | SHA 256 checksum of package |

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
