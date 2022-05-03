<div align="center">

<img src="https://kubernetes.io/images/wheel.svg" align="center" width="144px" height="144px"/>

# Home Ops
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![pre-commit](https://img.shields.io/badge/pre--commit-disabled-red?logo=pre-commit&logoColor=white&style=for-the-badge)](https://github.com/pre-commit/pre-commit)
[![renovate](https://img.shields.io/github/workflow/status/simbleau/home-ops/Schedule%20-%20Renovate?label=renovate&logo=renovatebot&style=for-the-badge)](https://github.com/onedr0p/home-ops/actions/workflows/)

[![internet](https://img.shields.io/uptimerobot/status/m791626909-5410cf23ca18cabcf74e32fa?color=lightgray&label=my%20home%20internet&style=flat-square&logo=opnSense&logoColor=white)](https://uptimerobot.com)
[![website](https://img.shields.io/uptimerobot/status/m791626907-5129386a08c0539012946152?logo=googlechrome&logoColor=white&color=lightgray&label=my%20website&style=flat-square)](https://spencer.imbleau.com)
[![home assistant](https://img.shields.io/uptimerobot/status/m791626943-e78c1a531a0ebfe443491da8?logo=homeassistant&logoColor=white&color=lightgray&label=my%20home%20assistant&style=flat-square)](https://www.home-assistant.io/)

</div>

---

## 📖 Overview

This is a mono repository for my home infrastructure and Kubernetes cluster. I try to adhere to Infrastructure as Code (IaC) and GitOps practices using tools like [__Ansible__](https://www.ansible.com/), [__Terraform__](https://www.terraform.io/), [__Kubernetes__](https://kubernetes.io/), [__Flux__](https://fluxcd.io/), [__Renovate__](https://renovatebot.com/) and [__GitHub Actions__](https://github.com/features/actions). All tools chosen are completely free and at no cost to myself.

---

## 📁 Directories

- **k8s**: directory contains my [__Kubernetes__](https://kubernetes.io/) configuration and artifacts.
- **provision**: directory contains my [__Ansible__](https://www.ansible.com/) playbooks and roles for provisioning my home infrastructure.

---

## ⛵ Kubernetes
[![K3S](https://img.shields.io/badge/k3s-v1.23-brightgreen?style=for-the-badge&logo=kubernetes&logoColor=white)](https://k3s.io/)

I run a fully conformant [__Kubernetes__](https://kubernetes.io/) cluster at home with [__K3S__](https://k3s.io/), provisioned overtop bare-metal Ubuntu 22.04 using [__Ansible__](https://www.ansible.com/). This is a semi hyperconverged cluster (HCI), with workloads and block storage sharing the same available resources from a centralized hardware RAID 5 enclosure.

📘 _[__Click here__](./k8s/) to learn more about my cluster._

---

## 🏁 Provisioning

- [__k8s__](./provision/k8s/): Provision my kubernetes cluster.
- [__ubuntu-workstation__](./provision/k8s/): Provision my Ubuntu Workstation.

📙 _[__Click here__](./provision/) to see my [__Ansible__](https://www.ansible.com/) playbooks and roles for provisioning my home infrastructure._

---

## 🤖 GitOps

- [__Flux__](https://fluxcd.io/) watches my [`cluster`](./k8s/cluster/) folder and makes the changes to my cluster automatically, based on the YAML manifests.
- [__Renovate__](https://renovatebot.com/) watches the repository for dependency updates, and automatically generates PRs for them. Automerging is allowed.
- [__GitHub Actions__](https://github.com/features/actions) validates and tests push and merge requests for conflicts.
- [__GitHub Pages__](https://pages.github.com/) deploys my [`helm`](./k8s/helm/) folder as a [__Helm__](https://helm.sh) registry.

---

## 🔧 Hardware

| Device                      | Amt | OS Disk | Data Disk    | RAM   | OS           | Purpose             |
| --------------------------- | --- | ------- | ------------ | ----- | ------------ | ------------------- |
| ARRIS Surfboard SB6183      | 1   | N/A     | N/A          | 256MB | N/A          | Modem               |
| ASUS RT-AC68U               | 1   | N/A     | N/A          | 16GB  | ASUSWRT      | Router, oVPN, SMB   |
| Raspberry Pi 4B 2GB         | 1   | 32GB SD | N/A          | 2GB   | Ubuntu 22.04 | Kubernetes Master   |
| Raspberry Pi 4B 2GB         | 3   | 32GB SD | N/A          | 2GB   | Ubuntu 22.04 | Kubernetes Worker   |
| Raspberry Pi 3 Model B+     | 1   | 32GB SD | N/A          | 1GB   | Ubuntu 22.04 | Kubernetes Worker   |
| AC Infinity CLOUDPLATE T1-N | 1   | N/A     | N/A          | 64GB  | Ubuntu 22.04 | Air Cooling         |
| Kingston SATA 3 2.5" SSD    | 4   | N/A     | 240 GB       | N/A   | N/A          | SATA 3 Internal SSD |
| QNAP TR-004 4 Bay DAS       | 1   | N/A     | 720 GB RAID5 | N/A   | N/A          | RAID 5 DAS          |
| ADJ Products PC-100A PDU    | 1   | N/A     | N/A          | N/A   | N/A          | PDU                 |

---

## 🔏 License
This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.