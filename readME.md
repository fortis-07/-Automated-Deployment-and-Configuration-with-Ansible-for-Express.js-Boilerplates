# ExpressJS App Deployment with Ansible

This repository contains an Ansible playbook for deploying an ExpressJS application with PostgreSQL and Redis on a target host.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Configuration](#configuration)
- [Usage](#usage)
- [Playbook Tasks](#playbook-tasks)
- [Variables](#variables)
- [Security Considerations](#security-considerations)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

This Ansible playbook automates the deployment of an ExpressJS application, including the setup of PostgreSQL, Redis, Nginx as a reverse proxy, and system services for automatic startup.

## Prerequisites

- Ansible 2.9 or higher
- Target host running a Debian-based Linux distribution (e.g., Ubuntu)
- SSH access to the target host
- Sudo privileges on the target host

## Configuration

1. Clone this repository:
```bash
git clone https://github.com/yourusername/expressjs-ansible-deploy.git
```
cd main.yaml

2. Update the `hosts` file with your target host details:
[hng]
your_target_host ansible_user=your_ssh_user
3. Modify the variables in the playbook (`main.yml`) if needed.

## Usage
```bash
ansible-playbook -i host main.yml
```

Run the playbook using the following command:

## Playbook Tasks

The playbook performs the following main tasks:

1. Installs necessary packages (Git, PostgreSQL, Python3-pip, etc.)
2. Configures PostgreSQL and creates a database user
3. Installs Node.js using NVM and Yarn package manager
4. Clones the ExpressJS application repository
5. Sets up environment variables
6. Installs application dependencies
7. Configures Nginx as a reverse proxy
8. Creates and starts a systemd service for the application

## Variables

Key variables that you may want to modify:

- `pg_admin_user`: PostgreSQL admin username
- `pg_database`: Name of the database to be created
- `app_port`: Port on which the ExpressJS app will run
- `db_host`, `db_port`: Database connection details
- `redis_host`, `redis_port`: Redis connection details

## Security Considerations

- The playbook generates a random password for the PostgreSQL admin user and stores it in `/var/secrets/pg_pw.txt` on the target host.
- Ensure to secure your target host and restrict access to sensitive files.
- Consider using Ansible Vault for storing sensitive variables.

## Troubleshooting

If you encounter any issues:

1. Check the Ansible output for error messages.
2. Verify the logs in `/var/log/stage_5b/` on the target host.
3. Ensure all prerequisites are met and the target host is accessible.
