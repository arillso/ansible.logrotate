# Ansible Role: logrotate

[![Build Status](https://img.shields.io/travis/arillso/ansible.logrotate.svg?branch=master&style=popout-square)](https://travis-ci.org/arillso/ansible.logrotate) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=popout-square)](https://sbaerlo.ch/licence) [![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-logrotate-blue.svg?style=popout-square)](https://galaxy.ansible.com/arillso/logrotate) [![Ansible Role](https://img.shields.io/ansible/role/d/23110.svg?style=popout-square)](https://galaxy.ansible.com/arillso/logrotate)

## Description

Installs and configures logrotate.

## Installation

```bash
  ansible-galaxy install arillso.logrotate
```

## Requirements

None.

## Role Variables

### include files

Path to the include files.

```yml
logrotate_include_dir: /etc/logrotate.d
```

### logrotate_global_config

Enable/disable global configuration of `/etc/logrotate.conf`.

```yml
logrotate_global_config: true
```

### logrotate_use_hourly_rotation

Enable/disable hourly rotation with cron.

```yml
logrotate_use_hourly_rotation: false
```

### logrotate options

List of global options.

```yml
logrotate_options:
  - weekly
  - rotate 4
  - create
  - dateext
  - su root syslog
```

### Package

Package name to install `logrotate`.

```yml
logrotate_package: logrotate
```

### default config

Logrotate for `wtmp`:

```yml
logrotate_wtmp_enable: true
logrotate_wtmp:
  logs:
    - /var/log/wtmp
  options:
    - missingok
    - monthly
    - create 0664 root utmp
    - rotate 1
```

Logrotate for `btmp`:

```yml
logrotate_btmp_enable: true
logrotate_btmp:
  logs:
    - /var/log/btmp
  options:
    - missingok
    - monthly
    - create 0660 root utmp
    - rotate 1
```

### Applications config

More log files can be added that will logorate.

```yml
logrotate_applications: []
```

#### Example

The following options are available.

```yml
logrotate_applications:
  - name: name-your-log-rotate-application
    definitions:
      - logs:
          - /var/log/apt/term.log
          - /var/log/apt/history.log
        options:
          - su user group
          - rotate 12
          - monthly
          - missingok
          - notifempty
        postrotate:
          - /path/to/some/script
```

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
    - arillso.logrotate
```

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2019, Arillso
