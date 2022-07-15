<div align="center">

<img src="https://simpleicons.org/icons/k3s.svg" width="144px" height="144px"/>

# K3S Cluster
[![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my [__K3S__](https://k3s.io/) cluster.

---

## 📁 Directories
- [__`inventory`__](./inventory/): Ansible hosts and environment variables.
- [__`playbooks`__](./playbooks/): Ansible playbooks and automation.
- [__`roles`__](./playbooks/): Ansible roles.

---

## 🏁 Provisioning Steps
- [ ] Install [SOPS](https://github.com/mozilla/sops) for sensitive file decryption (**required**)
  > Releases: [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)
- [ ] Mount access to the SOPS `keys.txt`
- [ ] Set the file path of the SOPS keys:
  > `export SOPS_AGE_KEY_FILE="/mnt/../sops/age/keys.txt"`
- [ ] Install ansible
  > `sudo apt install ansible`
- [ ] Install ansible requirements
  > `ansible-galaxy install -r requirements.yml`
- [ ] Run provisioning playbook
  > `ansible-playbook ./playbooks/provision.yml`
