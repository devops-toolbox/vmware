Role Name
=========

vmware: Vmware

[![Build Status](https://travis-ci.org/cmihai-ansible/vmware.svg?branch=master)](https://travis-ci.org/cmihai-ansible/vmware)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.vmware](https://galaxy.ansible.com/devops-toolbox.vmware)

```bash
ansible-galaxy install devops-toolbox.vmware
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
vmware_packages_state: present
vmware_remove_packages: true
vmware_enable_service: true
vmware_enable_selinux: true
vmware_copy_templates: true
vmware_firewall_configure: true
vmware_firewall_rules:
  - service: ssh
  - port: 3389
vmware_users:
  - user: devops
    group: docker
vmware_selinux_booleans:
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
- name: Install vmware on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: vmware is configured
      import_role:
        name: devops-toolbox.vmware
      vars:
        vmware_packages_state: present
        vmware_remove_packages: true
        vmware_enable_service: true
        vmware_enable_selinux: true
        vmware_copy_templates: true
        vmware_firewall_configure: true
        vmware_firewall_rules:
          - service: ssh
          - port: 3389
        vmware_users:
          - user: devops
            group: docker
        vmware_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: vmware
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
