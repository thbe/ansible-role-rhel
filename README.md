# Ansible Role thbe-rhel

[![Ansible Lint](https://github.com/thbe/ansible-role-rhel/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/thbe/ansible-role-rhel/actions/workflows/ansible-lint.yml)[![Molecule](https://github.com/thbe/ansible-role-rhel/actions/workflows/molecule.yml/badge.svg)](https://github.com/thbe/ansible-role-rhel/actions/workflows/molecule.yml)

This role configures and deploys base settings on an RHEL instance or RHEL clone.

## Requirements

To unlock the full potential of this role, you need to be registered in the RHN and subscribed to at least a standard RHEL subscription.

## Role Variables

* **role_directory** - This variable contains the root path of the directories used by thbe roles (**do not change!**)
* **net_manage** - Manage local network (default: false)
* **net_mtu** - Set the MTU size (default: 1500)
* **net_connection_prefix** - Prefix for network connection names (default: 'System ')
* **net_interface** - Name of the network interface (default: 'eth0')
* **net_hostname_primary** - Primary host name (default: not defined)
* **net_hostname_secondary** - Secondary hostname/ alias (default: not defined)
* **net_ip_primary** - Primary IP address (default: not defined)
* **net_ip_secondary** - Secondary IP address (default: not defined)
* **net_route_1** - Additional route 1 (default: not defined)
* **net_route_2** - Additional route 2 (default: not defined)
* **net_gw** - Standard gateway (default: not defined)
* **net_packages:** - List of packages required for NetworkManager
* **cockpit_packages** - List of packages required for Cockpit
* **rhn_manage** - Manage RHN subscriptions (default: false)
* **rhn_organization_id** - RHN organization ID (default: 'unset')
* **rhn_activation_key** - RHN activation key (default: 'unset')
* **rhn_pool_id** - RHN pool ID (default: 'unset')
* **rhel_release_version** - Locked RHEL release version (default: 'latest')
* **rhel_kernel_version** - Locked RHEL kernel version (default: 'latest')
* **rhel_repos_8** - List of standard RHEL 8 repositories
* **rhel_repos_9** - List of standard RHEL 9 repositories
* **rhel_packages_common** - List of standard RHEL packages
* **rhel_packages_8** - List of standard packages for RHEL 8 only
* **rhel_packages_rhn** - List of standard packages for RHN only
* **external_repos_epel** - Enables EPEL repository (default: false)

## Dependencies

This role depends on:

* thbe.common

## Example Playbook

This role can be included in the site.yml like this:

```yaml
# Site playbook
- name: Ansible playbooks for all nodes
  hosts: all
  collections:
    - ansible.posix
    - community.general
  gather_facts: true
  tasks:
    - name: "Include thbe.common"
      ansible.builtin.include_role:
        name: "thbe.common"
    - name: "Include thbe.rhel"
      ansible.builtin.include_role:
        name: "thbe.rhel"
      vars:
        external_repos_epel: true
```

## License

GPL-3.0-only

## Author Information

Thomas Bendler - [https://www.thbe.org/](https://www.thbe.org/)
