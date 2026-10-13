# Ansible Security Lab
This is my personal lab for learning Ansible. I'm building the environment from scratch and adding new playbooks step by step.

## Lab Environment
The lab currently consists of two Ubuntu Server virtual machines running in VirtualBox.
| Server | Role | Operating System |
|---|---|---|
| Server 1 (`ansible-controller`) | Ansible control node | Ubuntu Server |
| Server 2 (`host1`) | Managed host | Ubuntu Server |

### VirtualBox Setup
Each server runs in its own virtual machine. The machines are connected through a host-only network so they can communicate with each other and with the host computer.

Components:
- **Virtualization:** Oracle VirtualBox
- **Operating system:** Ubuntu Server
- **Automation:** Ansible
- **Remote access:** SSH
- **Managed host connection:** SSH from Server 1 to Server 2

### SSH Connection
Ansible runs on Server 1 and connects to Server 2 over SSH. This allows me to execute commands and manage the second server without logging in to it for every task.

I tested the connection with:
```bash
ansible -i inventory/hosts.ini managed -m ping
```
A successful connection returns `pong`.

## Project Structure
The project files are stored on Server 1 in `~/ansible-security-lab`.

```text
ansible-security-lab/
├── inventory/
│   └── hosts.ini
├── playbooks/
│   ├── gather_info.yml
│   ├── install_curl.yml
│   └── manage_users.yml
├── .gitignore
└── README.md
```

- `inventory/hosts.ini` contains the managed hosts.
- `playbooks/` contains the playbooks.

## Current Playbooks

### 1. Gather System Information
**File:** `playbooks/gather_info.yml`

Collects information about the managed server using Ansible facts.

Run with:
```bash
ansible-playbook -i inventory/hosts.ini playbooks/gather_info.yml
```

### 2. Install curl
**File:** `playbooks/install_curl.yml`

Installs the `curl` package on the managed server.

Run with:
```bash
ansible-playbook -i inventory/hosts.ini playbooks/install_curl.yml -K
```

### 3. Manage Users
**File:** `playbooks/manage_users.yml`

Manage users and permissions.

Run with:
```bash
ansible-playbook -i inventory/hosts.ini playbooks/manage_users.yml -K
```

## Planned Playbooks
- [ ] **System updates** – automate package updates and maintenance
- [ ] **SSH security** – check and manage SSH server settings
- [ ] **Firewall management** – configure and verify firewall rules
- [ ] **Linux hardening** – apply basic security settings
- [ ] **Service management** – check, configure and restart system services
- [ ] **User and group management** –
