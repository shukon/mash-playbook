# Firezone

[Firezone](https://www.firezone.dev/) is a self-hosted VPN server (based on [WireGuard](https://en.wikipedia.org/wiki/WireGuard)) with Web UI that this playbook can install, powered by the [moan0s/role-firezone](https://github.com/moan0s/role-firezone) Ansible role.

## Configuration

To enable this service, add the following configuration to your `vars.yml` file and re-run the [installation](../installing.md) process:

```yaml
########################################################################
#                                                                      #
# firezone                                                             #
#                                                                      #
########################################################################

firezone_enabled: true

firezone_hostname: vpn.example.org

firezone_default_admin_email: "user@invalid.org"
firezone_default_admin_password: "<securepassword>"

# Generate this with `openssl rand -base64 32`
firezone_database_encryption_key: "<secret>"

########################################################################
#                                                                      #
# /firezone                                                            #
#                                                                      #
########################################################################
```

After installation, you can use `just run-tags firezone-create-or-reset-admin` any time to:
- create the configured admin account
- or, reset the password to the current password configured in `vars.yml`

### Networking

By default, the following ports will be exposed by the container on **all network interfaces**:

- `51820` over **UDP**, controlled by `firezone_wireguard_bind_port` - used for [Wireguard](https://en.wikipedia.org/wiki/WireGuard) connections

Docker automatically opens these ports in the server's firewall, so you **likely don't need to do anything**. If you use another firewall in front of the server, you may need to adjust it.

### Usage

After [installing](../installing.md), you can login at the URL specified in `firezone_hostname`, with the credentials set in `firezone_default_admin_email` and `firezone_default_admin_password`.

Refer to the [official documentation](https://www.firezone.dev/docs/user-guides/add-devices/) to figure out how to add devices, etc.