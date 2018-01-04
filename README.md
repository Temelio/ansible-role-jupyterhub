# jupyterhub

[![Build Status](https://travis-ci.org/Temelio/ansible-role-jupyterhub.svg?branch=master)](https://travis-ci.org/Temelio/ansible-role-jupyterhub)

Install jupyterhub package.

## Requirements

This role requires Ansible 2.2 or higher,
and platform requirements are listed in the metadata file.

## Testing

This role use [Molecule](https://github.com/metacloud/molecule/) to run tests.

Local and Travis tests run tests on Docker by default.
See molecule documentation to use other backend.

Currently, tests are done on:
- Debian Jessie
- Ubuntu Trusty
- Ubuntu Xenial

and use:
- Ansible 2.2.x
- Ansible 2.3.x
- Ansible 2.4.x

### Running tests

#### Using Docker driver

```
$ tox
```

## Role Variables

### Default role variables

``` yaml
# Package management
jupyterhub_apt_update_cache: True
jupyterhub_apt_cache_valid_time: 3600
jupyterhub_system_dependencies: "{{ _jupyterhub_system_dependencies | default([]) }}"
jupyterhub_pip_packages:
  - name: 'jupyterhub'
    version: '0.8.1'

# Install method
# * pip: use python packages on pypi
jupyterhub_install_method: 'pip'
jupyterhub_install_globally: True
jupyterhub_manage_system_dependencies: True
```

### Debian OS family role variables

``` yaml
_jupyterhub_system_dependencies:
  - name: 'git'
  - name: 'python3-pip'
```

## Dependencies

None

## Example Playbook

``` yaml
- hosts: servers
  roles:
    - { role: Temelio.jupyterhub }
```

## License

MIT

## Author Information

Alexandre Chaussier (for Temelio company)
- http://www.temelio.com
- alexandre.chaussier [at] temelio.com
