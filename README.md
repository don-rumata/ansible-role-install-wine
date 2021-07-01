# Ansible Role: Install Wine

[![License][license-image]][license-url] [![Ansible Galaxy][ansible-galaxy-image]][ansible-galaxy-url] [![CircleCI][circleci-image]][circleci-url] [![Ansible Galaxy Quality][ansible-galaxy-quality-image]][ansible-galaxy-url]

Install [Wine](https://winehq.org) for Linux.

## Work on

```yaml
  platforms:
    - name: Fedora
      versions:
        - 33
    - name: Ubuntu
      versions:
        - focal
        - bionic
        - xenial
    - name: Debian
      version:
        - jessie
        - stretch
        - buster
        - stable
        - testing
    - name: EL (CentOS)
      versions:
        - 8
        - 7
    - name: opensuse
      vesrion:
        - tumbleweed
    - name: ArchLinux
      version:
        - any
```

## Requirements

`min_ansible_version: 2.6`

## Role Variables

None.

## Dependencies

None.

## Example Playbook

`install-wine.yml`:

```yaml
- name: Install Wine
  hosts: all
  strategy: free
  serial:
    - "100%"
  roles:
    - ansible-role-install-wine
  tasks:
```

## License

Apache License, Version 2.0

## Author Information

[don Rumata](https://github.com/don-rumata)

## TODO

- ~~Add tests.~~
- Add more tests.

[license-image]: https://img.shields.io/github/license/don-rumata/ansible-role-install-wine.svg
[license-url]: https://opensource.org/licenses/Apache-2.0

[ansible-galaxy-image]: https://img.shields.io/badge/ansible_galaxy-don__rumata.ansible__role__install__wine-blue.svg
[ansible-galaxy-url]: https://galaxy.ansible.com/don_rumata/ansible_role_install_wine

[circleci-image]: https://circleci.com/gh/don-rumata/ansible-role-install-wine.svg?style=shield
[circleci-url]: https://circleci.com/gh/don-rumata/ansible-role-install-wine

[ansible-galaxy-quality-image]: https://img.shields.io/ansible/quality/48079
