# Ansible Role: logrotate
[![Build Status](https://travis-ci.org/arillso/ansible.logrotate.svg?branch=master)](https://travis-ci.org/arillso/ansible.logrotate)

## Description

Installs and configures logrotate

## Installation

```
$ ansible-galaxy install arillso.logrotate
```

## Requirements

None

## Role Variables

| Variable             | Default     | Comments (type)                                   |
| :---                 | :---        | :---                                              |
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

## Changelog

### 1.1

* add become support

### 1.0

* inital role

## Author

* [Simon Bärlocher](https://sbaerlocher.ch)
 
## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2017, Simon Bärlocher