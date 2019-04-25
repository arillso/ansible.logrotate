# Ansible Role: logrotate

[![Build Status](https://img.shields.io/travis/arillso/ansible.logrotate.svg?branch=master&style=popout-square)](https://travis-ci.org/arillso/ansible.logrotate) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=popout-square)](https://sbaerlo.ch/licence) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-logrotate-blue.svg?style=popout-square)](https://galaxy.ansible.com/arillso/logrotate) [![Ansible Role](https://img.shields.io/ansible/role/d/23110.svg?style=popout-square)](https://galaxy.ansible.com/arillso/logrotate)

## Description

Installs and configures logrotate

## Installation

```bash
  ansible-galaxy install arillso.logrotate
```

## Requirements

None

## Role Variables

| Variable               | Default                                                                                             | Comments (type)                          |
| :--------------------- | :-------------------------------------------------------------------------------------------------- | :--------------------------------------- |
| logrotate_options      | [ 'weekly', 'su root syslog', 'rotate 4', 'create' ]                                                | List of default options                  |
| logrotate_wtmp         | { logs: ['/var/log/wtmp'], options: ['missingok', 'monthly', 'create 0664 root utmp', 'rotate 1'] } | Logrotate options for wtmp               |
| logrotate_btmp         | { logs: ['/var/log/btmp'], options: ['missingok', 'monthly', 'create 0660 root utmp', 'rotate 1'] } | Logrotate options for btmp               |
| logrotate_applications | []                                                                                                  | Logrotate options for other applications |

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
    - arillso.logrotate
```

### Example

```yml
logrotate_applications:
  - name: zabbix-agent
    definitions:
      - logs:
          - '/var/log/zabbix/zabbix_agentd.log'
        options:
          - weekly
          - rotate 13
          - compress
          - delaycompress
          - missingok
          - notifempty
          - create 0640 zabbix zabbix
  - name: nginx
    definitions:
      - logs:
          - '/var/log/nginx/nginx.log'
        options:
          - weekly
          - rotate 13
          - compress
          - delaycompress
          - missingok
          - notifempty
          - create 0640 www-data adm
```

## Changelog

### 1.4.1

- add Red Hat Support

### 1.4

- update loop_vars
- add defaults vars

### 1.3

- new role tests

### 1.2

- rename role

### 1.1

- add become support

### 1.0

- inital role

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2019, Simon Bärlocher
