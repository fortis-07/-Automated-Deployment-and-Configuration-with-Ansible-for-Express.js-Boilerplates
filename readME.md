# Automated Deployment and Configuration with Ansible for Boilerplates

## Overview

This project focuses on automating the deployment and configuration of a boilerplate application using Ansible. The goal is to configure an instance of the chosen boilerplate by utilizing Infrastructure as Code (IaC) with Ansible to streamline setup and management tasks.

## Project Goals

The deployment process includes:

1. **Cloning the Repository**:
   - Cloning the `devops` branch of the specified boilerplate repository to a remote Ubuntu 22.04 server.

2. **Installing Dependencies and Deploying**:
   - Installing necessary dependencies such as PostgreSQL and RabbitMQ.
   - Building and deploying the boilerplate application.

3. **Setting Up PostgreSQL**:
   - Configuring a PostgreSQL database and storing credentials securely.

4. **Configuring Messaging Queue**:
   - Setting up RabbitMQ and managing user permissions.

5. **Application Configuration**:
   - Ensuring the application runs on port 3000 and setting up Nginx to reverse proxy to port 80.

6. **Configuring Logging**:
   - Setting up logging to capture stderr and stdout logs.

## Instructions

### User and Directory Setup

- **Create User**:
  - Creates a user named `hng` with sudo privileges.

- **Clone Repository**:
  - Clones the devops branch of the repository into `/opt/stage_5b` and assigns ownership to the `hng` user.

### Database and Dependencies

- **Install PostgreSQL**:
  - Installs PostgreSQL, creates a user and database, and stores credentials in `/var/secrets/pg_pw.txt`.

- **Install RabbitMQ**:
  - Installs RabbitMQ, enables the management plugin, and sets up users and permissions.

- **Install Dependencies**:
  - Installs Node.js using NVM and sets up other necessary dependencies.

### Application and Proxy Setup

- **Start Application**:
  - Configures the application to run on `127.0.0.1:3000`.

- **Install and Configure Nginx**:
  - Installs Nginx and configures it to reverse proxy requests from port 80 to port 3000.

### Logging Configuration

- **Setup Logging**:
  - Configures PM2 to handle logging, ensuring stderr and stdout logs are written to specified paths.

## File Structure

- `/var/secrets/pg_pw.txt`: Contains PostgreSQL credentials.
- `/var/secrets/rabbitmq_creds.txt`: Contains RabbitMQ credentials.
- `/var/log/stage_5b/`: Directory for application logs (`error.log` and `out.log`).
- `/opt/stage_5b/`: Directory where the boilerplate repository is cloned.

## Requirements

- Ansible 2.9 or higher
- Ubuntu 22.04 server
- Node.js (installed via NVM)
- PostgreSQL
- RabbitMQ
- Nginx
- PM2

## Usage

1. **Prepare the Server**:
   - Ensure you have a remote Ubuntu 22.04 server with SSH access.

2. **Run the Ansible Playbook**:
   - Clone this repository.
   - Navigate to the repository directory.
   - Run the playbook using the following command:
     ```bash
     sudo ansible-playbook -i <your_inventory_file> main.yml
     ```

     
