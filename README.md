# Ansible Role: caddyserver

## Description

Install and configure caddyserver using ansible.

## Requirements

- Ansible >= 2.5 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

The default webroot folder is `/var/www` and the default logfolder is `/var/log/caddy`

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `caddy_user` | caddy | Caddy user |
| `caddy_group` | caddy | Caddy group |
| `caddy_logrotate_days` | 28 | Caddy logrotate rotate days |
| `caddy_default_http_port` | 80 | Caddy default http port |
| `caddy_basic_auth` | true | Caddy enable basic auth |
| `caddy_basic_auth_user` | proxy | Caddy basic auth user |
| `caddy_basic_auth_pass` | "JDJhJDE0JHJ0VEF6ZldHWEI5RWs3UUk1amptL09mcVRua0I5QmI1SFlZL3ltRTBJN0twek02Zi9FdE11" | Caddy basic auth pass (generate with caddy hash-paddword |
| `caddy_basic_auth_paths` | "/socks.html /squid.html /squid_acls" | Caddy basic auth pathes |

## Example

```yaml
---
# Define caddyserver custom vhosts
caddy_config:
  - name: custom
    http_port: 8081
    folder: /var/www/<folder>
    # caddy.custom.conf
    content: |
      root * /var/www/<folder>
      file_server
```

### Playbook

```yaml
---
- hosts: all
  roles:
  - ansible-role-caddyserver
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
