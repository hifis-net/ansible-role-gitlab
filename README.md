<!--
SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

# GitLab Ansible Role

:warning: **This project is archived!** :warning:

This role has been migrated to our `hifis.toolkit` collection:

- <https://github.com/hifis-net/ansible-collection-toolkit>
- <https://galaxy.ansible.com/ui/repo/published/hifis/toolkit/>

[![CI Status](https://github.com/hifis-net/ansible-role-gitlab/actions/workflows/ci.yml/badge.svg)](https://github.com/hifis-net/ansible-role-gitlab/actions/workflows/ci.yml)
[![Ansible Galaxy Role](https://img.shields.io/ansible/role/53362?color=orange)](https://galaxy.ansible.com/hifis/gitlab)
[![Ansible Galaxy Role downloads](https://img.shields.io/ansible/role/d/53362)](https://galaxy.ansible.com/hifis/gitlab)
[![Ansible Galaxy quality score](https://img.shields.io/ansible/quality/53362)](https://galaxy.ansible.com/hifis/gitlab)
[![Apache-2.0 Licensed](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/hifis-net/ansible-role-gitlab/blob/main/LICENSES/Apache-2.0.txt)
[![Latest release](https://img.shields.io/github/v/release/hifis-net/ansible-role-gitlab)](https://github.com/hifis-net/ansible-role-gitlab/releases)

A role to install and configure official GitLab Omnibus package.

Currently [supported platforms](meta/main.yml) are:

- CentOS 7
- AlmaLinux 8
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS (Bionic Beaver)
- Ubuntu 20.04 LTS (Focal Fossa)
- Ubuntu 22.04 LTS (Jemmy Jellyfish)

## Requirements

None.

## Role Variables

### Important Role Variables

#### GitLab Edition

The GitLab edition to install. Please use either `gitlab-ce` for Community
Edition or `gitlab-ee` for Enterprise Edition.

```yaml
gitlab_edition: "gitlab-ee"
```

#### GitLab Version and Release

Set a specific GitLab version to install. Please ensure that you also specify
the desired release. You can find the available releases
[here](https://packages.gitlab.com/gitlab).

```yaml
gitlab_version: "15.6.1"

# GitLab Release for RHEL/AlmaLinux 8
gitlab_release: "ce.0.el8"

# GitLab Release for Ubuntu
gitlab_release: "ce.0"
```

**Please note:** If no GitLab version is specified the role will always install
the latest available GitLab package.

#### GPG Key URL

URL to the GPG key that was used to sign the packages.

```yaml
gitlab_gpg_key_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/gpgkey"
```

#### GPG Key ID

Identifier of GPG key that was used to sign the packages.

```yaml
gitlab_gpg_key_id: "F6403F6544A38863DAA0B6E03F01618A51312F3F"
```

#### Package Repository URL

URL to the package repository based on the operating system.

```yaml
gitlab_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/ubuntu/"
```

#### Source Package Repository URL

URL to the source package repository (*CentOS* and *AlmaLinux* only).

```yaml
gitlab_source_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/el/{{ ansible_facts.distribution_major_version }}/SRPMS"
```

#### Package Name

Name of the GitLab package to install.

```yaml
gitlab_package_name: "{{ gitlab_edition + '=' + gitlab_version + '-' + gitlab_release if gitlab_version and gitlab_release else gitlab_edition }}"
```

#### Package Dependencies

List of depend packages required by GitLab based on the operating system.

```yaml
gitlab_dependencies:
  - apt-transport-https
  - curl
  - gnupg
  - openssh-server
  - openssl
  - tzdata
```

#### URL of your GitLab Instance

Give the URL of your GitLab instance:

```yaml
gitlab_external_url: 'https://gitlab.example.com'
```

#### Timezone to Be Used by GitLab

Choose the timezone to be used by GitLab:

```yaml
gitlab_time_zone: 'Europe/Berlin'
```

#### Period of Time to Keep Backups

Set the period of time (in seconds) to keep your GitLab backups:

```yaml
gitlab_backup_keep_time: '604800'
```

### Optional Role Variables

#### Name of Template for GitLab's Configuration File

Specify the name of the template for GitLab's configuration file which 
will be transformed into GitLab's configuration file:

```yaml
gitlab_configuration_file_template: 'gitlab.rb.j2'
```

#### Path to GitLab's Configuration File

Specify the path of the template for GitLab's configuration file which 
contains custom configurations of your GitLab instance:

```yaml
gitlab_configuration_file_path: '/etc/gitlab/gitlab.rb'
```

#### GitLab Theme to Be Used by Default

Choose the Default Theme to be used for new GitLab users:

```yaml
gitlab_default_theme: '2'
```

#### Path to GitLab Backups

Set the path to the GitLab backups:

```yaml
gitlab_backup_path: '/var/opt/gitlab/backups'
```

#### Port on Which Web-Server Nginx is Listening on

Set the port GitLab's web-server Nginx is listening on:

```yaml
gitlab_nginx_listen_port: '80'
```

#### Does Web-Server Nginx accept HTTPS Requests?

Choose whether GitLab's web-server Nginx accepts HTTPS requests:

```yaml
gitlab_nginx_listen_https: 'false'
```

#### Does Web-Server Nginx Redirect HTTP Requests to HTTPS?

Choose whether GitLab's web-server Nginx redirects HTTP requests to HTTPS:

```yaml
gitlab_nginx_redirect_http_to_https: 'false'
```

#### Set GitLab feature flags

Set [GitLab feature flags](https://docs.gitlab.com/ee/user/feature_flags.html)
to enable or disable additional features.
The variable is a list of key-value pairs which requires the `name` of the
feature flag and its boolean state `enabled`.
The default value is set to an empty list `[]`.

```yaml
gitlab_feature_flags:
  - name: "vscode_web_ide"
    enabled: true
  - name: "chatops"
    enabled: true
  - name: "webauthn"
    enabled: false  
```

#### Mattermost only use case

This role can be used to run Mattermost without deploying GitLab. In this
scenario services like _sidekiq_ or _puma_ are not required. Set to `true` to
prevent the role from reloading those services:

```yaml
gitlab_mattermost_only_context: 'false'
```

### Variables to be Set if External Redis is Used

#### Switch to Use External Redis Instance

Set switch to `false` to enable external Redis instance:

```yaml
gitlab_use_internal_redis: 'false'
```

#### Password to Authenticate Redis Services within Cluster

It is recommended to enable authentication for Redis Master and Redis Replicas
by providing the respective password:

```yaml
gitlab_redis_password: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### Password to Authenticate Redis Sentinels

Support for Redis Sentinel password authentication was introduced in GitLab 16.1.

```yaml
gitlab_redis_sentinel_password: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### Reference Name of the Redis Cluster

Choose a name of the Redis Cluster for references:

```yaml
gitlab_redis_cluster_name: 'redis-cluster'
```

#### List of IP addresses of Redis Sentinel Servers

Add a list of IP addresses of the involved Redis Sentinel servers:

```yaml
gitlab_redis_sentinel_ips:
  - '192.168.33.11'
  - '192.168.33.12'
  - '192.168.33.13'
```

#### Port on Which Redis Sentinel Servers are Listening

Choose port on which Redis Sentinel servers are listening:

```yaml
gitlab_redis_sentinel_port: '26379'
```

#### Whitelist IP Address Range for Monitoring Redis Sentinel Servers

Range of GitLab IP addresses that are allowed to monitor Redis Sentinel servers:

```yaml
gitlab_ip_range: '{{ ansible_facts.default_ipv4.address }}/24'
```

### Variables to be Set if External Gitaly is Used

#### Switch to Use External Gitaly Instance

Set switch to `false` to enable external Gitaly instance:

```yaml
gitlab_use_internal_gitaly: 'false'
```

#### Path to GitLab Data Directory

Specify where to put the GitLab data directory:

```yaml
gitlab_git_data_dir: "/var/opt/gitlab/git-data"
```

#### Gitaly Authentication Token

A Gitaly authentication token needs to be given:

```yaml
gitlab_gitaly_token: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### GitLab Shell Token

A GitLab shell token needs to be given:

```yaml
gitlab_secret_token: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### Gitaly IP Address

Specify IP address of the Gitaly instance:

```yaml
gitlab_gitaly_instance_ip: '127.0.0.1'
```

#### Gitaly Port

Specify port of the Gitaly instance:

```yaml
gitlab_gitaly_instance_port: '8075'
```

### Variables to be Set if External PostgreSQL Database is Used

#### Switch to Use External PostgreSQL Database Instance

Set switch to `false` to enable external PostgreSQL Database instance:

```yaml
gitlab_use_internal_postgresql: 'false'
```

#### IP Address of External PostgreSQL Database Instance

Set IP Address of PostgreSQL Database instance:

```yaml
gitlab_postgresql_db_host: '127.0.0.1'
```

#### Password for External PostgreSQL Database Instance

Set password of PostgreSQL Database instance:

```yaml
gitlab_postgresql_db_password: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### Configure GitLab Registry

Enable GitLab container registry:
```yaml
gitlab_registry_enable: "true"
```

_Please note_: If you do not run a load balancer in front of GitLab and let
NGinx care about SSL encryption, please also configure
`registry_nginx['ssl_certificate']` and `registry_nginx['ssl_certificate_key']`
via `gitlab_additional_configurations`.

### Additional Configurations given as Role Variables

Any other configurations that are not yet part of GitLab's configuration file
can be given by Ansible role variables.

#### Configurations via Dictionary-like Ruby Variables

Ruby variables that are not part of GitLab's configuration file
can be given by Ansible role variables.

**Code Attribution / Terms of Use:**

This idea of
[generic key-value pairs](https://github.com/geerlingguy/ansible-role-gitlab/blob/master/templates/gitlab.rb.j2)
is attributed to the work of 
[Jeff Geerling](https://github.com/geerlingguy)
which is originally licensed under the MIT License.

**Usage example:**

```yaml
gitlab_additional_configurations:
  - gitlab_rails:
      - key: "time_zone"
        value: "Europe/Berlin"
  - nginx:
      - key: "listen_port"
        type: "plain"
        value: "80"
      - key: "listen_https"
        type: "plain"
        value: "false"
```

**Resulting configuration:**

```ruby
gitlab_rails['time_zone'] = 'Europe/Berlin'
nginx['listen_port'] = 80
nginx['listen_https'] = false
```

#### Configurations via Ruby Function Calls

Ruby function calls that are not part of GitLab's configuration file
can be given by Ansible role variables.

**Usage example:**

```yaml
gitlab_ruby_configuration_calls:
  - key: "pages_external_url"
    value: "https://pages.example.com"
  - key: "registry_external_url"
    value: "https://registry.example.com"
  - key: "mattermost_external_url"
    value: "https://mattermost.example.com"
```

**Resulting configuration:**

```ruby
registry_external_url "https://registry.example.com"
pages_external_url "https://pages.example.com"
mattermost_external_url "https://mattermost.example.com"
```

## Dependencies

None.

## License

[Apache-2.0](LICENSES/Apache-2.0.txt)

## Author Information

[HIFIS Software Team](https://software.hifis.net)

## Contributors

We would like to thank and give credits to the following contributors of this
project:

* [flyinggecko](https://github.com/flyinggecko)
