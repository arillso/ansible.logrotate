# Changelog

This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
and [human-readable changelog](https://keepachangelog.com/en/1.0.0/).

## master

## 1.6.1

### Fixed

- Fix typos (imclude -> include)
- Fix role name

### Changed

- Extended example

## 1.6.0

### Fixed

- Travis CI and molecule setup.
- The src option requires state to be 'link' or 'hard' (breaking in Ansible
  2.10) (Fixes: #14).

### Changed

- `logrotate_use_hourly_rotation` will no longer clean the symlink in
  `cron.daily`.
- Bumped tested distros versions.

### Added

- Options to enable or not wtmp/btmp config by [smutel](https://github.com/smutel)
  via PR #25 (Fixes: #23).
- Option to skip global configuration file by [fhsctv](https://github.com/fhsctv)
  via PR #28.

## 1.5.2

### Fixed

- Fix custom definition of logrotate_options via inventory

## 1.5.1

### Fixed

- Incorrect documentation adapted.

## 1.5.0

### Changed

- Updated min ansible version to 2.8
- Changelog has been moved to its own file
- Travis file has been updated
- Documentation has been improved

### Added

- molecule testing
- hourly rotation option

## 1.4.1

### Added

- add Red Hat Support

## 1.4.0

### Changed

- update loop_vars

### Added

- add defaults vars

## 1.3.0

### Changed

- new role tests

## 1.2.0

### Changed

- rename role

## 1.1.0

### Added

- add become support

## 1.0.0

### Added

- inital Release
