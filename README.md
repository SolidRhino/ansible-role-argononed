# Ansible Role: argononed

This role installs and configures the argononed daemon for Raspberry Pi hardware.

## Description

The argononed daemon is designed to control the fan and power button of Argon ONE cases for Raspberry Pi. This role will automatically detect if it's running on Raspberry Pi hardware and install/configure the daemon accordingly.

## Requirements

### Hardware
- Raspberry Pi (verified through device tree)
- Argon ONE case

### Software
- Ansible collections:
  - community.general

### Operating Systems
- Raspberry Pi OS
- RetroPie
- Manjaro-arm
- Arch Linux ARM
- Ubuntu
- OSMC
- TwisterOS
- DietPI
- Pop OS
- Kali Linux
- AlmaLinux
- openSUSE
- Fedora IoT
- Fedora Server

## Role Variables

Available variables are listed below, along with default values:

```yaml
# Repository URL for the argononed daemon
argononed_repo: "https://gitlab.com/DarkElvenAngel/argononed.git"

# Version of argononed to install
argononed_version: "v1.3.1"
```

## Important Notes

1. This role will automatically enable the i2c interface if it's not already enabled
2. If i2c was not previously enabled, the system will automatically reboot to apply the changes
3. The role will automatically skip execution if it detects that it's not running on Raspberry Pi hardware
4. The installation script requires root privileges
5. The role requires the community.general collection for package management on some distributions

## Installation

### As a Collection Role

You can install this role and its dependencies with:

```bash
ansible-galaxy collection install community.general
ansible-galaxy role install <your-role-name>
```

### As a Git Submodule

You can also include this role as a Git submodule in your Ansible project:

```bash
git submodule add https://github.com/SolidRhino/ansible-role-argononed.git roles/ansible-role-argononed
git submodule update --init --recursive
```

Example directory structure when using submodules:
```
your-ansible-project/
├── inventory/
├── group_vars/
├── host_vars/
├── roles/
│   └── ansible-role-argononed/  # Added as submodule
└── playbook.yml
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: raspberry_pi
  roles:
    - ansible-role-argononed
```

## Example Inventory

```ini
[raspberry_pi]
argon-pi ansible_host=192.168.1.100
```

## Configuration

After installation, the daemon configuration can be found at `/etc/argononed.conf`.

## License

MIT

## Author Information

Your Name <your.email@example.com>

## Bug Reports & Feature Requests

Please submit bug reports and feature requests to the [issue tracker](your-repository-url/issues).
