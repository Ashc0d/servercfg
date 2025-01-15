# servercfg: Ansible Playbook for Configuring and Securing Debian-Based Linux Servers

## Overview

This Ansible playbook is designed to automate the configuration and security hardening of Debian-based Linux servers. It streamlines the setup process, ensuring consistency and compliance with best practices.

## Status

**Note:** This playbook is currently under development. Features and functionalities are being actively added and tested.

## Compatibility

- **Supported Operating Systems:** Debian-based distributions (e.g., Ubuntu)

## Prerequisites

- **Ansible:** Ensure Ansible is installed on your control machine. Installation instructions can be found in the [Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

- **Configuration Variables:** A config.yml file contains all the variables required for server configuration. You can customize it based on your needs before running the playbook.

- **Hosts Inventory:** Create a `inventory` file in the project directory to define your target nodes.

  Example `inventory`:

  ```ini
  [servers]
  server1 ansible_host=192.168.1.10 ansible_user=your_user
  server2 ansible_host=192.168.1.11 ansible_user=your_user
  ```

## Usage

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/Ashc0d/servercfg.git
   cd servercfg
   ```

2. **Configure Inventory:**

   Edit the `inventory` file with your server details as shown in the example above.

3. **Run the Playbook:**

   - To apply the playbook to all servers:

     ```bash
     ansible-playbook playbook.yml -i inventory -K
     ```

   - To target a specific server:

     ```bash
     ansible-playbook playbook.yml -i inventory --limit=server1 -K
     ```

   - To run the playbook locally:

     ```bash
     ansible-playbook playbook.yml -i inventory --connection=local -K
     ```

   **Note:** The `-K` flag prompts for the become (sudo) password, which is required for tasks that require elevated privileges.

4. **Update Servers:**

   To update packages on the servers:

   ```bash
   ansible-playbook -i inventory playbook.yml --tags=update -K -e reboot_confirmation=no
   ```

## Features

- **Security Hardening:** Configures SSH settings to enhance security.
- **Package Management:** Installs and updates necessary packages.
- **Service Management:** Ensures critical services are enabled and running.
- **System Updates:** Automates the process of updating the system packages.

## License

This project is licensed under the Apache License, Version 2.0, January 2004. See the [LICENSE](LICENSE) file for details.

---

For more information and detailed documentation, please refer to the [official repository](https://github.com/Ashc0d/servercfg). 