# Ansible Role: RPM Fusion

![Ansible Galaxy](https://github.com/0x022b/ansible-role-rpmfusion/workflows/Ansible%20Galaxy/badge.svg)

Ansible role that configures [RPM Fusion][rpmfusion] free and nonfree repositories.

## Requirements

None.

## Role Variables

Available variables are listed below with default values.

```yaml
rpmfusion_free_package_state: present
rpmfusion_nonfree_package_state: absent
```

Variables to control the state of free and nonfree repository packages.

## Dependencies

- 0x022b.epel

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: 0x022b.rpmfusion
```

## Versioning

This project uses [Semantic Versioning][semver].

## License

MIT

[rpmfusion]: https://rpmfusion.org/
[semver]: https://semver.org/
