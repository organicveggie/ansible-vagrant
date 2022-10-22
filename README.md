# organicveggie.ansible-vagrant

Ansible role to install Vagrant on Linux using standard OS and distribution packages.

|GitHub|Issues|Pull Requests|
|---|---|---|
|[![github](https://github.com/organicveggie/ansible-vagrant/workflows/Molecule/badge.svg)](https://github.com/organicveggie/ansible-vagrant/actions)|[![Issues](https://img.shields.io/github/issues/organicveggie/ansible-vagrant.svg)](https://github.com/organicveggie/ansible-vagrant/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/organicveggie/ansible-vagrant.svg)](https://github.com/organicveggie/ansible-vagrant/pulls/)|

## Supported Platforms

* CentOS/RedHat 8
* Debian buster, bullseye
* Fedora 33, 34
* Ubuntu 18.04, 20.04, 22.04

## Role Variables

General defaults are set in `defaults/main.yml`. 

```yaml
# The URL of the GPG key for repository validation.
vagrant_gpg_key_url: https://apt.releases.hashicorp.com/gpg

# The name of the package which contains Vagrant.
vagrant_package_name: "vagrant" 
```

OS and distro defaults are set in
`vars/*.yml`.

```yaml
# URL for the Vagrant repository, which will override the default value. Default URLs are shown
# in the table below.
vagrant_repository_url_override: 
```

|Distro|URL|
|---|---|
|Debian|[https://apt.releases.hashicorp.com](https://apt.releases.hashicorp.com)|
|Fedora|[https://rpm.releases.hashicorp.com/fedora/hashicorp.repo](https://rpm.releases.hashicorp.com/fedora/hashicorp.repo)|
|RedHat|[https://rpm.releases.hashicorp.com/RHEL/$releasever/$basearch/stable](https://rpm.releases.hashicorp.com/RHEL/$releasever/$basearch/stable)|

## Sample Playbooks

### Simple

```yaml
- hosts: all
  roles:
    - role: orgaanicveggie.vagrant
```

### Overrideas

```yaml
- hosts: developers
  roles:
    - role: orgaanicveggie.vagrant
      vars:
        vagrant_gpg_key_url: "https://myserver.example.com/gpg"
        vagrant_package_name: "vagrant-custom"
        vagrant_repository_url_override: "https://apt.myserver.example.com"
```
