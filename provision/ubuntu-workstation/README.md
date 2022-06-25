<div align="center">

<img src="https://simpleicons.org/icons/ubuntu.svg" width="144px" height="144px"/>

# Ubuntu Workstation
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![ubuntu version](https://img.shields.io/badge/22.04-E95421?style=for-the-badge&logo=ubuntu&label=Ubuntu&logoColor=white)](https://releases.ubuntu.com/22.04/)
[![Ansible](https://img.shields.io/badge/ansible%205-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my [__Ubuntu 22.04 Jammy Jellyfish__](https://releases.ubuntu.com/22.04/) workstation.

---

## 📁 Directories
- [__`inventory`__](./inventory/): Ansible hosts and environment variables.
- [__`playbooks`__](./playbooks/): Ansible playbooks and automation.
- [__`roles`__](./playbooks/): Ansible roles.

---

## 🏁 Provisioning Steps
- [ ] Install SOPS for data encryption (**required**)
  > [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)
- [ ] Mount a secure device with access to the SOPS `keys.txt` file
- [ ] Export the file path to the shell
  > `export SOPS_AGE_KEY_FILE="/mnt/../sops/age/keys.txt"`
- [ ] Install ansible
  > `sudo apt install ansible`
- [ ] Install ansible requirements
  > `ansible-galaxy install -r requirements.yml`
- [ ] Run provisioning playbook
  > `ansible-playbook ./playbooks/provision.yml`
