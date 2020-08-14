<!--
SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

GitLab Role
===========

Ansible role to configure GitLab Omnibus installation.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role 
should be mentioned here. For instance, if the role uses the EC2 module, 
it may be a good idea to mention in this section that the boto package is 
required.

Role Variables
--------------

### Mandatory Role Variables with No Defaults

There are no role variables without defaults, but you should carefully choose
the important role variables described in the next section.

### Important Role Variables

###### URL of your GitLab Instance

Give the URL of your GitLab instance:

```yaml
gitlab_external_url: 'http://localhost'
```

###### Timezone to Be Used by GitLab

Choose the timezone to be used by GitLab:

```yaml
gitlab_time_zone: 'Europe/Berlin'
```

###### Period of Time to Keep Backups

Set the period of time (in seconds) to keep your GitLab backups:

```yaml
gitlab_backup_keep_time: '604800'
```

### Optional Role Variables

###### Name of Template for GitLab's Configuration File

Specify the name of the template for GitLab's configuration file which 
will be transformed into GitLab's configuration file:

```yaml
gitlab_configuration_file_template: 'gitlab.rb.j2'
```

###### Path to GitLab's Configuration File

Specify the path of the template for GitLab's configuration file which 
contains custom configurations of your GitLab instance:

```yaml
gitlab_configuration_file_path: '/etc/gitlab/gitlab.rb'
```

###### GitLab Theme to Be Used by Default

Choose the Default Theme to be used for new GitLab users:

```yaml
gitlab_default_theme: '2'
```

###### Path to GitLab Backups

Set the path to the GitLab backups:

```yaml
gitlab_backup_path: '/var/opt/gitlab/backups'
```

###### Port on Which Web-Server Nginx is Listening on

Set the port GitLab's web-server Nginx is listening on:

```yaml
nginx_listen_port: '80'
```

###### Does Web-Server Nginx accept HTTPS Requests?

Choose whether GitLab's web-server Nginx accepts HTTPS requests:

```yaml
nginx_listen_https: 'false'
```

###### Does Web-Server Nginx Redirect HTTP Requests to HTTPS?

Choose whether GitLab's web-server Nginx redirects HTTP requests to HTTPS:

```yaml
nginx_redirect_http_to_https: 'false'
```

### Variables to be Set if External Redis is Used

###### Switch to Use External Redis Instance

```yaml
use_internal_redis: 'false'
```

###### Password to Authenticate Redis Services within Cluster

You have to use your own private and encrypted password here:

```yaml
redis_password: 'changeme'
```

###### Reference Name of the Redis Cluster

Choose a name of the Redis Cluster for references:

```yaml
redis_cluster_name: 'redis-cluster'
```

###### List of IP addresses of Redis Sentinel Servers

Add a list of IP addresses of the involved Redis Sentinel Servers:

```yaml
redis_sentinel_ips:
  - '192.168.33.11'
  - '192.168.33.12'
  - '192.168.33.13'
```

###### Port on Which Redis Sentinel Servers are Listening

Choose port on which Redis Sentinel Servers are listening:

```yaml
redis_sentinel_port: '26379'
```

###### Whitelist the GitLab IP Address for Redis Sentinel Servers

Range of IP addresses of GitLab instances needs to be white-listed for the 
involved Redis Sentinel Servers:

```yaml
gitlab_ip_range: '{{ ansible_default_ipv4.address }}/24'
```

### Additional Configurations given as Role Variables

Any other key-value pair that is not yet part of GitLab's configuration file
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

Dependencies
------------

This GitLab Role depends on 
[GitLab Base Role](https://gitlab.com/hifis/ansible/gitlab-base-role.git) 
which installs the GitLab Omnibus package.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

[Apache-2.0](LICENSES/Apache-2.0.txt)

Author Information
------------------

HIFIS Software Team (please visit [HIFIS Software Webpage](https://software.hifis.net))
