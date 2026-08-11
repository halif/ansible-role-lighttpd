# Ansible Role: Lighttpd

[![Ansible Integration](https://img.shields.io/badge/ansible-2.12+-blue.svg)](https://docs.ansible.com/)
[![Molecule Tested](https://img.shields.io/badge/molecule-tested-green.svg)](https://molecule.readthedocs.io/)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)

An Ansible role that installs, configures, and manages the **Lighttpd** web server on Debian/Ubuntu, RHEL/Rocky Linux, and OpenSUSE.

## Requirements

No special requirements. Note that for Enterprise Linux (RHEL/Rocky Linux), the **EPEL** repository must be enabled on the target host before applying this role, as `lighttpd` is not available in the default base repositories.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
lighttpd_package_name: lighttpd
# The name of the package to install.

lighttpd_service_name: lighttpd
# The name of the systemd service.

lighttpd_service_state: started
# The desired state of the Lighttpd service (started, stopped, restarted).

lighttpd_service_enabled: true
# Whether the service should start on boot.

lighttpd_port: 80
# The port Lighttpd will listen on.

lighttpd_server_root: /var/www/html
# The document root directory for your website.
```

## Dependencies

None.

## Example Playbook

Inside your playbook file (e.g., `playbook.yml`):

```yaml
- hosts: webservers
  become: true
  roles:
    - role: halif.ansible_role_lighttpd
```

You can also pass variables to customize the installation:

```yaml
- hosts: webservers
  become: true
  vars:
    lighttpd_port: 8080
    lighttpd_server_root: /var/www/my_custom_app
  roles:
    - role: halif.ansible_role_lighttpd
```

## Local Development & Testing

This role uses **Molecule** with a Docker driver for automated matrix testing across multiple distributions (Ubuntu 22.04, Rocky Linux 9, OpenSUSE 15).

To run the local test suite:

```bash
pip install molecule[docker] ansible-core
molecule test
```

## License

MIT

## Author Information

Created by **halif** (Ildar).  
GitHub Repository: [ansible-role-lighttpd](https://github.com)
