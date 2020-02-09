Role Name
=========

lvm: Lvm

[![Build Status](https://travis-ci.org/cmihai-ansible/lvm.svg?branch=master)](https://travis-ci.org/cmihai-ansible/lvm)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.lvm](https://galaxy.ansible.com/devopstoolbox.lvm)

```bash
ansible-galaxy install devopstoolbox.lvm
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
lvm_packages_state: present
lvm_remove_packages: true
lvm_enable_service: true
lvm_enable_selinux: true
lvm_copy_templates: true
lvm_firewall_configure: true
lvm_firewall_rules:
  - service: ssh
  - port: 3389
lvm_users:
  - user: devops
    group: docker
lvm_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install lvm on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: lvm is configured
      import_role:
        name: devopstoolbox.lvm
      vars:
        lvm_packages_state: present
        lvm_remove_packages: true
        lvm_enable_service: true
        lvm_enable_selinux: true
        lvm_copy_templates: true
        lvm_firewall_configure: true
        lvm_firewall_rules:
          - service: ssh
          - port: 3389
        lvm_users:
          - user: devops
            group: docker
        lvm_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: lvm
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
