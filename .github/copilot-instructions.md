# Project Guidelines

## Overview

Ansible project for provisioning and configuring a GCP Ubuntu VM (SSOPMS).

## Architecture

- `playbook.yml` — Main playbook targeting the `ssopms` host group
- `inventory/hosts.ini` — Static inventory with GCP VM IP and SSH config
- `ansible.cfg` — Ansible configuration (inventory path, privilege escalation)

## Build and Test

```bash
# Verify connectivity
ansible ssopms -m ping

# Dry-run the playbook
ansible-playbook playbook.yml --check --diff

# Run the playbook
ansible-playbook playbook.yml
```

## Conventions

- Target OS: Ubuntu on GCP
- SSH: key-based auth via `~/.ssh/id_ed25519`, user `martin.lord`
- Use fully qualified collection names (e.g., `ansible.builtin.apt`)
- All playbooks use `become: true` for privilege escalation
- Keep tasks idempotent
