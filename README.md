# Ansible Collection - snowdrop.cloud_infra

Manages OpenStack VMs.

## Requirements

* `openstack.cloud` Ansible Collection

## Role Variables

OpenStack VM role required parameters

| Parameter   | Comments                          |
|-----------------|--------|
| `openstack_auth` <br/><span style="color:fuchsia">map</span> / <span style="color:red">required</span> | Map with the authentication |
| `openstack_security_group` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Security group |
| `state` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | State of the VM <br/> * `present` <br/> * `absent` |
| `vm_name` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Name of the VM to be created |

For the `openstack_auth` Map parameter, the required contents are the following.

| Name  | Comments                          |
|-------|-----------------------------------|
| `openstack_project_name` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Tenant domain |
| `openstack_console_user` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Console login user |
| `openstack_console_password` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Console login user |
| `openstack_user_domain`      <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | User domain |
| `openstack_project_domain`   <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Project domain |
| `openstack_os_auth_url`      <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Service authentication URL |

Output: 
* `openstack_vm_ipv4`
* `openstack_output`

## Example

Sample playbook:

```yaml
- name: "Create VM on OpenStack"
  hosts: localhost
  gather_facts: True

  tasks:
    - name: "Create VM"
      ansible.builtin.include_role:
        name: "snowdrop.cloud_infra.openstack_vm"
        vars:
          openstack_auth:
            openstack_project_name: 
            openstack_console_user: 
            openstack_console_password: 
            openstack_user_domain: 
            openstack_project_domain: 
            openstack_os_auth_url: 
          state: present
          vm_name: snowdrop-vm
```