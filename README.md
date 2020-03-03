# Ansible Role: `aisbergg.stubby`

This is Ansible role installs and configures the DNS Privacy stub resolver Stubby.

## Requirements

None.

## Role Variables

| Variable | Default | Comments |
|----------|---------|----------|
| `stubby_service_state` | `started` | Set the service state (Possible values: started, reloaded, restarted, stopped) | 
| `stubby_service_enabled` | `true` | Enable/Disable the Stubby service | 
| `stubby_config` | `{}` | Dictionary of Stubby configuration variables (key-value pairs). A list of available variables and their documentation can be found in [`vars/main.yml`](vars/main.yml). |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  vars: 
    stubby_service_state: started
    stubby_service_enabled: true
    stubby_config:
      upstream_recursive_servers:
        # Quad 9 'secure' service - Filters, does DNSSEC, doesn't send ECS
        - address_data: 9.9.9.9
          tls_auth_name: "dns.quad9.net"
        - address_data: 2620:fe::fe
          tls_auth_name: "dns.quad9.net"
  roles:
    - aisbergg.stubby
```

## License

MIT

## Author Information

Andre Lehmann (aisberg@posteo.de)
