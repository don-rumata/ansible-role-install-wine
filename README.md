# Ansible Role: Install Wine

[![License][license-image]][license-url] [![Ansible Galaxy][ansible-galaxy-image]][ansible-galaxy-url] [![CircleCI][circleci-image]][circleci-url] [![Ansible Galaxy Quality][ansible-galaxy-quality-image]][ansible-galaxy-url]

Install [Wine](https://winehq.org) for Linux.

## Work on

```yaml
  platforms:
    - name: Fedora
      versions:
        - 33
        - 34
    - name: Ubuntu
      versions:
        - xenial
        - bionic
        - focal
    - name: Debian
      version:
        - stretch
        - buster
        - sid
    - name: opensuse
      vesrion:
        - tumbleweed
        - 15.3
```

## Requirements

`min_ansible_version: 2.6`

## Role Variables

```yaml
#--- Version section ---#

wine_branch: stable
# wine_branch: devel
# wine_branch: staging

# wine_package_name: wine
# wine_package_name: winehq-stable
# wine_package_name: wine-mono
# wine_package_name: wine-nine-standalone-32bit
# wine_package_name: wine-staging-devel-32bit-debuginfo
# wine_package_name: any-package-you-like

wine_install_winetricks: true
# wine_install_winetricks: false

#--- Repo section ---#

wine_gpg_key: https://dl.winehq.org/wine-builds/winehq.key
wine_repo_deb_key: '{{ wine_gpg_key }}'
wine_repo_rpm_key: '{{ wine_gpg_key }}'

# If you *NOT* use apt-cacher-ng or other caching proxy - select "https".
http_or_https: http
# http_or_https: https
```

## Dependencies

None.

## HowTo

### How to install role

Over `ansible-galaxy`:

```bash
ansible-galaxy install don_rumata.ansible_role_install_wine
```

Over `bash+git`:

```bash
mkdir -p "$HOME/.ansible/roles"
cd "$HOME/.ansible/roles"
git clone https://github.com/don-rumata/ansible-role-install-wine don_rumata.ansible_role_install_wine
```

## Example Playbook

### I

Install `wine` and `winetricks` on any [supported](#work_on) Linux:

`install-wine.yml`:

```yaml
- name: Install Wine
  hosts: all
  strategy: free
  serial:
    - "100%"
  roles:
    - don_rumata.ansible_role_install_wine
  tasks:
```

### II

Install only `wine`, without `winetricks`:

`install-wine.yml`:

```yaml
- name: Install Wine
  hosts: all
  strategy: free
  serial:
    - "100%"
  roles:
    - role: don_rumata.ansible_role_install_wine
      wine_install_winetricks: false
  tasks:
```

### III

Install `wine-devel-amd64`, without `winetricks`:

`install-wine.yml`:

```yaml
- name: Install Wine
  hosts: all
  strategy: free
  serial:
    - "100%"
  roles:
    - role: don_rumata.ansible_role_install_wine
      wine_install_winetricks: false
      wine_package_name: wine-devel-amd64
  tasks:
```

## License

Apache License, Version 2.0

## Author Information

[don Rumata](https://github.com/don-rumata)

## TODO

- ~~Add tests.~~
- Add more tests.
- Add `wine-gecko`.

[license-image]: https://img.shields.io/github/license/don-rumata/ansible-role-install-wine.svg
[license-url]: https://opensource.org/licenses/Apache-2.0

[ansible-galaxy-image]: https://img.shields.io/badge/ansible_galaxy-don__rumata.ansible__role__install__wine-blue.svg
[ansible-galaxy-url]: https://galaxy.ansible.com/don_rumata/ansible_role_install_wine

[circleci-image]: https://circleci.com/gh/don-rumata/ansible-role-install-wine.svg?style=shield
[circleci-url]: https://circleci.com/gh/don-rumata/ansible-role-install-wine

[ansible-galaxy-quality-image]: https://img.shields.io/ansible/quality/55561
