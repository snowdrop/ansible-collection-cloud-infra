# Role: OpenStack VM

Manages OpenStack VMs.

## Description

This role will provision and remove OpenStack VMs.

## Requirements

Ansible Collections:

```yaml
collections:
  - name: openstack.cloud
    version: 2.1.0
```

## Role Variables

OpenStack VM role parameters

| Parameter | Comments   |
|-----------|------------|
| `rhos_auth` <br/><span style="color:fuchsia">map</span> / <span style="color:red">required</span> | Map with the authentication |
| `rhos_auth_type` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | RHOS Authentication type  <sup>1)</sup> |
| `openstack_security_group` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Security group |
| `state` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | State of the VM <br/> * `present` <br/> * `absent` |
| `vm_name` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Name of the VM to be created |
| `openstack_vm_auto_floating_ip` <br/>$\color{fuchsia}{\textsf{string}}$ | Auto associate a Floating IP <br/> * **`false` <= Default** <br/> * `true` |

<sup>1)</sup> More information on the available keystone plugins on the 
[RHOS documentation](https://docs.openstack.org/keystoneauth/latest/plugin-options.html#available-plugins).
 
The `rhos_auth` Map parameter must contain the required attributes for a successfull 
 authentication as selected with the `rhos_auth_type` variable. 
 
For a `v3password` authentication the required contents are the following.

| Name  | Comments                          |
|-------|-----------------------------------|
| `auth_url`      <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Service authentication URL |
| `password` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Console login user |
| `project_domain_name`   <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Project domain |
| `project_name` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Tenant domain |
| `user_domain_name`      <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | User domain |
| `username` <br/>$\color{fuchsia}{\textsf{map}}$ / $\color{red}{\textsf{required}}$ | Console login user |

Output: 
* `openstack_vm_ipv4`
* `openstack_output`

## Example Playbook

```yaml
- name: "Create VM on OpenStack"
  hosts: localhost
  gather_facts: True

  tasks:
    - name: "Create VM"
      ansible.builtin.include_role:
        name: "snowdrop.cloud_infra.openstack_vm"
        vars:
          state: present
          vm_name: snowdrop-vm
```

## License

Apache License 2.0

## Author Information

This role has been created by the [Snowdrop team](https://github.com/snowdrop/).
