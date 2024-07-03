# LinuxSecurityEnhancer

## Overview

`LinuxSecurityEnhancer` is an Ansible project designed to enhance the security of Linux servers. The project aims to provide various roles that implement security best practices and harden system configurations to protect against vulnerabilities and threats.

## Features

- Modular design with individual roles for different security aspects
- Easy integration into existing Ansible workflows
- Automated compliance checks
- Support for multiple Linux distributions

## Requirements

- Ansible 2.9+
- Supported Operating Systems: RedHat-like (AlmaLinux, Oracle Linux) versions 8 and 9, Debian 11

## Project Structure

The project structure is as follows:

```
LinuxSecurityEnhancer/
├── playbooks/
│   └── secure_ssh.yml
├── roles/
│   └── secure_ssh/
│       ├── tasks/
│       │   ├── main.yml
│       │   ├── ssh_config.yml
│       │   └── analyze_ssh_config.yml
│       ├── handlers/
│       │   └── main.yml
│       ├── README.md
│       └── meta/
│           └── main.yml
├── inventories/
│   ├── dev
│   └── prod
├── LICENSE
└── README.md
```

## Usage

To use the roles provided by `LinuxSecurityEnhancer`, include them in your Ansible playbooks. Each role is designed to be easily integrated and customizable to fit your security needs.

## Example Playbook

```yaml
---
- name: Secure Linux Servers
  hosts: all
  become: yes

  roles:
    - secure_ssh
    # Add other roles as they become available
```

## Roles

- **secure_ssh**: Secures SSH configurations according to security guidelines.

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/LinuxSecurityEnhancer.git
   ```

2. Navigate to the project directory:

   ```bash
   cd LinuxSecurityEnhancer
   ```

3. Update the inventory files in the `inventories` directory with your server details.

4. Run the playbook:

   ```bash
   ansible-playbook playbooks/secure_ssh.yml -i inventories/prod
   ```

## Note

**Disclaimer:** The use of these playbooks is at the user's own risk. It is essential that the user understands the changes being made to the system configurations. The authors and contributors cannot be held responsible for any issues that may arise from the use of these playbooks.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

## Author Information

This project was created by Philippe CANDIDO, an expert in automation and system administration using Ansible.

## Contributions

Contributions are welcome! Please submit a pull request or open an issue on the GitHub repository.

## Support

For any issues or questions, please open an issue on the GitHub repository or contact support@emerging-it.fr.