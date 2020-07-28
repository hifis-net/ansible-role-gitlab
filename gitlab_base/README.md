<!--
SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

# GitLab Base Role

This Ansible Role provides a basic setup for services based on GitLab Omnibus.

## Requirements

None.

## Role Variables

```yaml
gitlab_edition: "gitlab-ee"
```
The GitLab edition to install. Please use either `gitlab-ce` for Community
Edition or `gitlab-ee` for Enterprise Edition.

```yaml
gitlab_version: "13.2.1"
gitlab_release: "ce.0.el8"
```
Set a specific GitLab version to install. Please ensure that you also specify
the desired release. You can find the available releases
[here](https://packages.gitlab.com/gitlab).

```yaml
gitlab_gpg_key_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/gpgkey"
```
URL to the GPG key that was used to sign the packages.

```yaml
gitlab_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/ubuntu/"
```
URL to the package repository based on the operating system.

```yaml
gitlab_source_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/el/{{ ansible_distribution_major_version }}/SRPMS"
```
URL to the source package repository (*CentOS* only).

```yaml
gitlab_package_name: "{{ gitlab_edition + '=' + gitlab_version + '-' + gitlab_release if gitlab_version and gitlab_release else gitlab_edition }}"
```
Name of the GitLab package to install.

```yaml
gitlab_dependencies:
  - apt-transport-https
  - curl
  - gnupg
  - openssh-server
  - openssl
```
List of depend packages required by GitLab based on the operating system.

## Dependencies

None.

## Example Playbook
```yaml
- hosts: servers
  roles:
     - { role: username.rolename, x: 42 }
```
## License

[Apache-2.0](LICENSES/Apache-2.0.txt)

## Author Information

This role was created by [HIFIS Software Services](https://software.hifis.net/).
