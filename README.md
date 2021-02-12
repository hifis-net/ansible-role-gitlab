<!--
SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

# GitLab Role

Ansible role to configure GitLab Omnibus installation.

## Requirements

None.

## Role Variables

### Mandatory Role Variables with No Defaults

There are no role variables without defaults, but you should carefully choose
the important role variables described in the next section.

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
gitlab_version: "13.2.1"
gitlab_release: "ce.0.el8"
```

#### GPG Key URL

URL to the GPG key that was used to sign the packages.

```yaml
gitlab_gpg_key_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/gpgkey"
```

#### Package Repository URL

URL to the package repository based on the operating system.

```yaml
gitlab_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/ubuntu/"
```

#### Source Package Repository URL

URL to the source package repository (*CentOS* only).

```yaml
gitlab_source_repo_url: "https://packages.gitlab.com/gitlab/{{ gitlab_edition }}/el/{{ ansible_distribution_major_version }}/SRPMS"
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
nginx_listen_port: '80'
```

#### Does Web-Server Nginx accept HTTPS Requests?

Choose whether GitLab's web-server Nginx accepts HTTPS requests:

```yaml
nginx_listen_https: 'false'
```

#### Does Web-Server Nginx Redirect HTTP Requests to HTTPS?

Choose whether GitLab's web-server Nginx redirects HTTP requests to HTTPS:

```yaml
nginx_redirect_http_to_https: 'false'
```

### Variables to be Set if External Redis is Used

#### Switch to Use External Redis Instance

Set switch to `false` to enable external Redis instance:

```yaml
use_internal_redis: 'false'
```

#### Password to Authenticate Redis Services within Cluster

It is recommended to enable authentication for Redis Master, Redis Replica and 
Redis Sentinel by providing the respective password:

```yaml
redis_password: 'changeme'
```

_Caution: You have to use your own private and encrypted password here._

#### Reference Name of the Redis Cluster

Choose a name of the Redis Cluster for references:

```yaml
redis_cluster_name: 'redis-cluster'
```

#### List of IP addresses of Redis Sentinel Servers

Add a list of IP addresses of the involved Redis Sentinel servers:

```yaml
redis_sentinel_ips:
  - '192.168.33.11'
  - '192.168.33.12'
  - '192.168.33.13'
```

#### Port on Which Redis Sentinel Servers are Listening

Choose port on which Redis Sentinel servers are listening:

```yaml
redis_sentinel_port: '26379'
```

#### Whitelist IP Address Range for Monitoring Redis Sentinel Servers

Range of GitLab IP addresses that are allowed to monitor Redis Sentinel servers:

```yaml
gitlab_ip_range: '{{ ansible_default_ipv4.address }}/24'
```

### Variables to be Set if External Gitaly is Used

#### Switch to Use External Gitaly Instance

Set switch to `false` to enable external Gitaly instance:

```yaml
use_internal_gitaly: 'false'
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
gitaly_instance_ip: '127.0.0.1'
```

#### Gitaly Port

Specify port of the Gitaly instance:

```yaml
gitaly_instance_port: '8075'
```

### Variables to be Set if External PostgreSQL Database is Used

#### Switch to Use External PostgreSQL Database Instance

Set switch to `false` to enable external PostgreSQL Database instance:

```yaml
use_internal_postgresql: 'false'
```

#### IP Address of External PostgreSQL Database Instance

Set IP Address of PostgreSQL Database instance:

```yaml
postgresql_db_host: '127.0.0.1'
```

#### Password for External PostgreSQL Database Instance

Set password of PostgreSQL Database instance:

```yaml
postgresql_db_password: 'changeme'
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
