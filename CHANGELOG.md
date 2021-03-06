<!--
SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Group your changes into these categories:

`Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

## [1.0.1](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v1.0.1) - 2021-03-16

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v1.0.0...v1.0.1)

### Fixed
- Stop role execution after failed ``apt`` package installation
  ([!39](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/39)
  by [Normo](https://gitlab.com/Normo)).

## [1.0.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v1.0.0) - 2021-03-03

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.5.0...v1.0.0)

### Added

- Automate role import into Ansible Galaxy via GitHub Actions
  ([!34](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/34)
  by [Normo](https://gitlab.com/Normo)).
- Merge gitlab_base into gitlab role
  ([!32](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/32)
  by [Normo](https://gitlab.com/Normo)).
- Reconfigure GitLab if a previous reconfiguration had failed
  ([!35](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/35)
  by [Normo](https://gitlab.com/Normo)).

### Changed

- Upgrade project dependencies
  ([!33](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/33)
  by [Normo](https://gitlab.com/Normo)).
- Use fully qualified collection names
  ([!36](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/36)
  by [Normo](https://gitlab.com/Normo)).

## [0.5.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.5.0) - 2021-01-18

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.4.0...v0.5.0)

### Added

- Add handlers to restart puma and sidekiq
  ([!30](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/30)
  by [Normo](https://gitlab.com/Normo)).

## [0.4.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.4.0) - 2020-10-13

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.3.4...v0.4.0)

### Added
- Supply generic way to configure GitLab via Ansible variables that are translated to Ruby function calls
  ([!27](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/27)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

### Changed
- Improve and speed up the CI pipeline
  ([!24](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/24)
  by [tobiashuste](https://gitlab.com/tobiashuste)).
- Bump dependency Ansible to ansible = "~=2.10.0"
  ([!25](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/25)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [0.3.4](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.3.4) - 2020-09-24

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.3.3...v0.3.4)

### Fixed

- Create file skip-auto-backup on non-primary GitLab nodes
  ([!21](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/21)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).
- Split handler to reconfigure GitLab into one for primary and one for non-primary nodes
  ([!22](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/22)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [0.3.3](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.3.3) - 2020-09-10

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.3.2...v0.3.3)

### Fixed
- Rename role 'gitlab_base_role' to 'gitlab_base' in meta and requirements files
  ([!20](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/20)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [0.3.2](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.3.2) - 2020-09-10

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.3.1...v0.3.2)

### Fixed
- Handler 'Reconfigure GitLab' needs to listens to handler 'GitLab has been installed or upgraded'
  ([!19](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/19)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [0.3.1](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.3.1) - 2020-09-09

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.3.0...v0.3.1)

### Fixed
- Fix reconfigure handler not run when GitLab package is upgraded
  ([!17](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/17)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [0.3.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.3.0) - 2020-09-08

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.2.0...v0.3.0)

### Added
- Trigger GitLab reconfigure if GitLab package has been installed or upgraded
  ([!16](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/16)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [0.2.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.2.0) - 2020-08-26

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.1.1...v0.2.0)

### Added
- Implement a basic configuration for the container registry
  ([!14](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/14)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [0.1.1](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.1.1) - 2020-08-21

[List of commits](https://gitlab.com/hifis/ansible/gitlab-role/-/compare/v0.1.0...v0.1.1)

### Fixed
- Fix creation of skip-auto-reconfigure file
  ([!12](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/12)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [0.1.0](https://gitlab.com/hifis/ansible/gitlab-role/-/releases/v0.1.0) - 2020-08-20

### Added

Initial release of the Ansible GitLab Role.
