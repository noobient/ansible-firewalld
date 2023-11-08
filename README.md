# noobient.firewalld

## Synopsys

This role lets your pass services and/or ports via zones with interfaces or sources.

## Parameters

| Name | Required | Example | Description |
|---|---|---|---|
| `service` | no | `home-assistant` | Service to enable. If `port` is also defined, the service is created with the specified port. Therefore if you use built-in services, omit `port`, otherwise specify it. |
| `port` | no | `8080/tcp` | Port number and protocol to open. |
| `zone` | no | `dmz` | Zone to apply the changes to. If not specified, changes are applied to the default zone (`public` usually). A zone must have either a `source` or an `interface`. |
| `source` | no | `99.99.99.99` | IP address to add to the zone. |
| `interface` | no | `eth0` | Interface to add to the zone. |
| `fw_target` | no | `ACCEPT` | firewalld target to set for the specified `zone`. Normally shouldn't be required. |
| `k8s_node` | no | `false` | If `true`, configuration is completely skipped and firewalld is disabled. This can be useful if you configure several hosts and some of them are K8s nodes, where a firewall shouldn't be present in most cases. Therefore this is normally set on a host/group level. |
| `rate_limit` | no | `10/m` | If set, the service will be enabled with the specified rate limit. |
| `family` | no | `ipv6` | If set, the rule will be limited to the specified address family. Only applied if `rate_limit` is also set, otherwise ignored. Possible values are `ipv4`, `ipv6`. |
| `enabled` | no | `false` | If `false`, the specified service is disabled, instead of enabled. Defaults to `true`. |

## Examples

```yml
- include_role:
    name: noobient.firewalld
  vars:
    service: https

- include_role:
    name: noobient.firewalld
  vars:
    service: sshsec
    port: 922/tcp

- include_role:
    name: noobient.firewalld
  vars:
    zone: wireguard
    interface: wg0
    fw_target: ACCEPT
    rate_limit: 100/m
    family: ipv6
    enabled: false
```

## Return Values

N/A

## Support

| Platform | Support | Status |
|---|---|---|
| Linter | ✅ | [![Lint](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/lint.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/lint.yml) |
| AlmaLinux 8 | ✅ | [![AlmaLinux 8](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/almalinux-8.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/almalinux-8.yml) |
| AlmaLinux 9 | ✅ | [![AlmaLinux 9](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/almalinux-9.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/almalinux-9.yml) |
| Fedora 38 | ✅ | [![Fedora 38](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/fedora-38.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/fedora-38.yml) |
| Fedora 39 | ✅ | [![Fedora 39](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/fedora-39.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/fedora-39.yml) |
| Ubuntu 18.04 | ✅ | [![Ubuntu 18.04](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-18.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-18.04.yml) |
| Ubuntu 20.04 | ✅ | [![Ubuntu 20.04](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-20.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-20.04.yml) |
| Ubuntu 22.04 | ✅ | [![Ubuntu 22.04](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-22.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-firewalld/actions/workflows/ubuntu-22.04.yml) |
