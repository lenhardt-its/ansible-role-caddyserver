# Ansible Role: Caddyserver v2.3.0 (currently static file for amd64, arm64, armv7)

[![ubuntu-18](https://img.shields.io/badge/ubuntu-18.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![ubuntu-20](https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![debian-9](https://img.shields.io/badge/debian-9.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![debian-10](https://img.shields.io/badge/debian-10.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![centos-7](https://img.shields.io/badge/centos-7.x-orange?style=flat&logo=centos)](https://www.centos.org/)
[![centos-8](https://img.shields.io/badge/centos-8.x-orange?style=flat&logo=centos)](https://www.centos.org/)

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg?style=flat)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-caddyserver?style=flat)](https://github.com/OnkelDom/ansible-role-caddyserver/issues)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-caddyserver.svg?style=flat)](https://github.com/OnkelDom/ansible-role-caddyserver/tags)
[![GitHub action](https://github.com/OnkelDom/ansible-role-caddyserver/workflows/ansible-lint/badge.svg)](https://github.com/OnkelDom/ansible-role-caddyserver)

## Description

Install and configure caddyserver using ansible.

Plugins:
 * caddy-ext_ratelimit
 * caddy-yaml
 * caddy-cgi_v2
 * caddyserver_ntlm-transport
 * caddy-authz_v2
 * caddy-auth-portal
 * caddy-docker-proxy_plugin_v2
 * caddy2-proxyprotocol
 * caddy2-filter

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)
- Community Packages: `ansible-galaxy collection install community.general`

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

The default webroot folder is `/var/www` and the default logfolder is `/var/log/caddy`

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `caddy_user` | caddy | Caddy user |
| `caddy_group` | caddy | Caddy group |
| `caddy_logrotate_days` | 28 | Caddy logrotate rotate days |
| `caddy_default_http_port` | 80 | Caddy default http port |
| `caddy_config` | [] | caddy config |

## Example

### Playbook

```yaml
---
- hosts: all
  roles:
  - onkeldom.caddyserver
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
