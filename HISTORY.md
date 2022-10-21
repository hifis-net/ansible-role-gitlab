**Changed**

- Update Python dependencies and use Python 3.9 in GitLab CI
  ([!49](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/49)
  by [tobiashuste](https://gitlab.com/tobiashuste)).
- Add role variable to specify apt key identifier
  ([!50](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/50)
  by [Normo](https://gitlab.com/Normo)).

## [v1.1.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v1.1.0) - 2021-12-08

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v1.0.2...v1.1.0)

### Added

- Add galaxy namespace to role metadata
  ([!44](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/44)
  by [Normo](https://gitlab.com/Normo)).

### Changed

- Replace include with import_tasks
  ([!45](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/45)
  by [Normo](https://gitlab.com/Normo)).
- Bump Python dependencies to the latest versions
  ([!42](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/42)
  by [tobiashuste](https://gitlab.com/tobiashuste)).
- Prevent restarting puma and sidekiq services in Mattermost only context
  ([!46](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/46)
  by [Normo](https://gitlab.com/Normo)).
- Install latest available GitLab version if no version has been pinned
  ([!47](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/47)
  by [Normo](https://gitlab.com/Normo)).

## [v1.0.2](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v1.0.2) - 2021-06-29

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v1.0.1...v1.0.2)

### Fixed

- Allow initial dry-runs without causing role deployments to fail
  ([!41](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/41)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [v1.0.1](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v1.0.1) - 2021-03-16

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v1.0.0...v1.0.1)

### Fixed

- Stop role execution after failed ``apt`` package installation
  ([!39](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/39)
  by [Normo](https://gitlab.com/Normo)).

## [v1.0.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v1.0.0) - 2021-03-03

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.5.0...v1.0.0)

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

## [v0.5.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.5.0) - 2021-01-18

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.4.0...v0.5.0)

### Added

- Add handlers to restart puma and sidekiq
  ([!30](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/30)
  by [Normo](https://gitlab.com/Normo)).

## [v0.4.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.4.0) - 2020-10-13

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.3.4...v0.4.0)

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

## [v0.3.4](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.3.4) - 2020-09-24

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.3.3...v0.3.4)

### Fixed

- Create file skip-auto-backup on non-primary GitLab nodes
  ([!21](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/21)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).
- Split handler to reconfigure GitLab into one for primary and one for non-primary nodes
  ([!22](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/22)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [v0.3.3](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.3.3) - 2020-09-10

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.3.2...v0.3.3)

### Fixed

- Rename role 'gitlab_base_role' to 'gitlab_base' in meta and requirements files
  ([!20](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/20)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [v0.3.2](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.3.2) - 2020-09-10

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.3.1...v0.3.2)

### Fixed

- Handler 'Reconfigure GitLab' needs to listens to handler 'GitLab has been installed or upgraded'
  ([!19](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/19)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [v0.3.1](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.3.1) - 2020-09-09

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.3.0...v0.3.1)

### Fixed

- Fix reconfigure handler not run when GitLab package is upgraded
  ([!17](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/17)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [v0.3.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.3.0) - 2020-09-08

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.2.0...v0.3.0)

### Added

- Trigger GitLab reconfigure if GitLab package has been installed or upgraded
  ([!16](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/16)
  by [christian.hueser.hzdr](https://gitlab.com/christian.hueser.hzdr)).

## [v0.2.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.2.0) - 2020-08-26

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.1.1...v0.2.0)

### Added

- Implement a basic configuration for the container registry
  ([!14](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/14)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [v0.1.1](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.1.1) - 2020-08-21

[List of commits](https://github.com/hifis-net/ansible-role-gitlab/compare/v0.1.0...v0.1.1)

### Fixed

- Fix creation of skip-auto-reconfigure file
  ([!12](https://gitlab.com/hifis/ansible/gitlab-role/-/merge_requests/12)
  by [tobiashuste](https://gitlab.com/tobiashuste)).

## [v0.1.0](https://github.com/hifis-net/ansible-role-gitlab/releases/tag/v0.1.0) - 2020-08-20

### Added

Initial release of the Ansible GitLab Role.
