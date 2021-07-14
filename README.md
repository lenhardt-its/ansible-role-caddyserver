# Ansible Role: Caddyserver v2.3.0 (currently static file for amd64, arm64, armv7)

[![ubuntu-18](https://img.shields.io/badge/ubuntu-18.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![ubuntu-20](https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![debian-9](https://img.shields.io/badge/debian-9.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![debian-10](https://img.shields.io/badge/debian-10.x-orange?style=flat&logo=debian)](https://www.debian.org/)

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
| `caddy_system_group` | caddy | Caddy user |
| `caddy_system_user` | caddy | Caddy group |
| `caddy_logrotate_days` | 28 | Caddy logrotate rotate days |
| `caddy_binary_local_dir` | /usr/local/bin | default bin dir |
| `caddy_config` | [] | caddy config |
| `caddy_config_path` | /etc/caddy | default config dir |
| `caddy_log_path` | /var/log/caddy | default log dir |
| `caddy_data_path` | /var/www | default webroot |
| `caddy_storage_path` | /var/lib/caddy | caddy internal storage path |
| `caddy_auto_https` | on | default auto https on/off |
| `caddy_vhost_defaults` | [defaults/main.yml#L21](defaults/main.yml#L21) | default vhost params |
| `caddy_tls_dns_cloudflare_enabled` | false | enable cloudflare tls |
| `cloudflare_token` | xxx |  |
| `caddy_env_vars` | ['CLOUDFLARE_API_TOKEN={{ cloudflare_token }}'] | see defaults |
| `caddy_vhosts` | [] | define vhosts configs |

## Example

### Playbook

```yaml
---
- hosts: all
  roles:
  - onkeldom.caddyserver
  vars:
    caddy_vhosts:
      - name: site1
        hostname: site1.domain.tld
        proxy_host: http://10.0.0.1
        gzip: compress
        security_headers: true
        responds: ['/forbidden 403']
        rewrites: ['* /path{uri}']
      - name: site2
        hostname: site1.domain.tld
        template: custom_template.j2
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
