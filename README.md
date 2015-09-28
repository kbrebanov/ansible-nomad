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
| nomad_version   | 0.1.0                                                            | Version of Nomad to install |
| nomad_sha256sum | 6d48846e40a44449f2b84eb37f32859eff98468ebffef3b4475d7a060f14fa32 | SHA 256 checksum of package |

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
