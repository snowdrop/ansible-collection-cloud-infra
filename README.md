# Ansible Collection - snowdrop.cloud_infra

Cloud infrastructure provisioning.

* Manages OpenStack VMs

## Requirements

Ansible Collections:

```yaml
collections:
  - name: openstack.cloud
    version: 2.1.0
```

## Role Variables

OpenStack VM role required parameters

| Parameter | Comments   |
|-----------|------------|
| `rhos_auth` <br/><span style="color:fuchsia">map</span> / <span style="color:red">required</span> | Map with the authentication |
| `rhos_auth_type` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | RHOS Authentication type  <sup>1)</sup> |
| `openstack_security_group` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Security group |
| `state` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | State of the VM <br/> * `present` <br/> * `absent` |
| `vm_name` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Name of the VM to be created |

<sup>1)</sup> More information on the available keystone plugins on the 
[RHOS documentation](https://docs.openstack.org/keystoneauth/latest/plugin-options.html#available-plugins).
 
The `rhos_auth` Map parameter must contain the required attributes for a successfull 
 authentication as selected with the `rhos_auth_type` variable. 
 
For a `v3password` authentication the required contents are the following.

| Name  | Comments                          |
|-------|-----------------------------------|
| `auth_url`      <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Service authentication URL |
| `password` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Console login user |
| `project_domain_name`   <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Project domain |
| `project_name` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Tenant domain |
| `user_domain_name`      <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | User domain |
| `username` <br/><span style="color:fuchsia">string</span> / <span style="color:red">required</span> | Console login user |

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
          rhos_auth:
            auth_url: 
            project_name: 
            username: 
            password: 
            user_domain_name: 
            project_domain_name: 
          rhos_auth_type: v3password
          state: present
          vm_name: snowdrop-vm
```