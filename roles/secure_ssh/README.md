# `secure_ssh` Role

## Overview

The `secure_ssh` role provides tasks to secure SSH configurations on Linux servers according to the guidelines specified in CERTFR-2024-ALE-009. This role ensures that critical SSH directives are configured correctly to enhance the security of the server.

## Features

- Disables root login via SSH
- Disables password authentication
- Disables challenge-response authentication
- Sets maximum authentication tries to 3
- Disables X11 forwarding
- Disables DNS resolution
- Sets login grace time to 0
- Analyzes current SSH configuration compliance with defined security settings

## Requirements

- Ansible 2.9+
- Supported Operating Systems: RedHat-like (AlmaLinux, Oracle Linux) versions 8 and 9, Debian 11

## Role Variables

This role does not require any additional variables to be set. It operates based on predefined security configurations.

## Usage

To use the `secure_ssh` role, include it in your playbook as follows:

```yaml
---
- name: Secure SSH Service
  hosts: all
  become: yes

  roles:
    - secure_ssh
```

## Tags

You can use tags to run specific tasks within this role:

- `PermitRootLogin`
- `PasswordAuthentication`
- `ChallengeResponseAuthentication`
- `MaxAuthTries`
- `X11Forwarding`
- `UseDNS`
- `LoginGraceTime`
- `analyze`

Example command to run the analyze task:

```bash
ansible-playbook playbooks/secure_ssh.yml -i inventories/prod -t "analyze"
```

## Handlers

The role includes a handler to restart the SSH service whenever a configuration change is applied:

- `restart sshd`

## Tasks

- Ensure SSH configuration directory exists
- Backup current `sshd_config`
- Disable root login from SSH
- Disable password authentication
- Apply additional security configurations
- Set maximum authentication tries
- Disable X11 forwarding
- Disable DNS resolution
- Set login grace time to 0
- Analyze current SSH configuration compliance

## Analyze SSH Configuration

The `analyze` tag can be used to verify if the SSH configurations are correctly applied. It will output the compliance score and suggest rerunning the playbook with specific tags if any directive is not set correctly.

```yaml
ansible-playbook playbooks/secure_ssh.yml -i inventories/prod -t "analyze"
```

## Example Playbook

```yaml
---
- name: Secure SSH Service
  hosts: all
  become: yes

  roles:
    - secure_ssh
```

## Note

**Disclaimer:** The use of this playbook is at the user's own risk. It is essential that the user understands the changes being made to the SSH configuration. The authors and contributors cannot be held responsible for any issues that may arise from the use of this playbook.

## License

This role is licensed under the MIT License. See the LICENSE file for more details.

## Author Information

This role was created by Philippe CANDIDO, an expert in automation and system administration using Ansible.

## Contributions

Contributions are welcome! Please submit a pull request or open an issue on the GitHub repository.

## Support

For any issues or questions, please open an issue on the GitHub repository or contact support@emerging-it.fr.