
# Ansible Collection - snowdrop.cloud_infra

![](https://github.com/snowdrop/ansible-collection-cloud-infra/actions/workflows/pr.yml/badge.svg)
![](https://img.shields.io/github/release/snowdrop/ansible-collection-cloud-infra.svg)
![](https://img.shields.io/github/release-date/snowdrop/ansible-collection-cloud-infra.svg)
![](https://img.shields.io/github/repo-size/snowdrop/ansible-collection-cloud-infra.svg)
![](https://img.shields.io/github/license/snowdrop/ansible-collection-cloud-infra.svg)


Cloud infrastructure provisioning.

* Manages OpenStack VMs

## Ansible compatibility

This collection has been tested against Ansible `2.9.10`.

## Installation

To use this collection it must be first installed.

This can performed by using the Ansible CLI directly.

```bash
ansible-galaxy collection install snowdrop.cloud_infra
```

Another way to install this collection is using a `requirements.yml` file. 

```yaml
---
collections:
  - name: snowdrop.cloud_infra
```

Then install the this file using the following command.

```bash
ansible-galaxy collection install -r requirements.yml --upgrade
```

## Roles

* [openstack_vm](roles/openstack_vm): provision OpenStack virtual machines

## Usage

To create a VM on an OpenStack project check the [`create_vm` playbook](playbooks/create_vm.yml).

To remove a VM from an OpenStack project check the [`remove_vm` playbook](playbooks/create_vm.yml).

## License

Apache License 2.0

Check the [LICENSE](LICENSE) to view the full text.

## Author Information

This role has been created by the [Snowdrop team](https://github.com/snowdrop/).
