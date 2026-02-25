# makevms-installers

Ansible playbooks for [MakeVMs](https://github.com/awkto/makevms) — automated software installation and configuration on VMs through the UI.

## Usage

### Bootstrap from MakeVMs UI

1. Navigate to the **Playbooks** page
2. Click **Bootstrap Playbooks**
3. Playbooks will be cloned to your configured playbook directory

### Manual Installation

```bash
git clone https://github.com/awkto/makevms-installers.git /etc/makevms/playbooks/official
```

## Available Playbooks

### Basics
| Playbook | Description |
|----------|-------------|
| [install-docker](basics/install-docker.yml) | Install Docker Engine and Docker Compose |
| [install-nginx](basics/install-nginx.yml) | Install and configure Nginx web server |

### DevOps
| Playbook | Description |
|----------|-------------|
| [install-gitlab-ce](devops/install-gitlab-ce.yml) | Install GitLab Community Edition |
| [install-openbao](devops/install-openbao.yml) | Install OpenBao secrets manager |

### Security
| Playbook | Description |
|----------|-------------|
| [install-acme-sh](security/install-acme-sh.yml) | Install acme.sh and issue SSL certificates via ACME |

## Writing Custom Playbooks

1. Create a `.yml` playbook file in any subdirectory
2. Optionally create a matching `.meta.yml` file for better UX
3. MakeVMs will auto-discover playbooks and extract variables

### Metadata Format

```yaml
name: "My Playbook"
description: "What this playbook does"
category: "Category Name"

variables:
  my_variable:
    description: "What this variable controls"
    default: "default_value"
  my_secret:
    description: "A sensitive value"
    secret: true
```

### Variable Sources

When configuring playbooks in the MakeVMs UI, each variable can be sourced from:

- **VM Field** — auto-resolved from the target VM (hostname, fqdn, ip_address)
- **Saved Value** — stored per-playbook, reused across runs
- **Prompt** — entered by the user each time the playbook runs

## License

MIT
