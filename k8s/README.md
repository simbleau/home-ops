<div align="center">

<img src="https://kubernetes.io/images/wheel.svg" align="center" width="144px" height="144px"/>

# Kubernetes
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![K3S](https://img.shields.io/badge/k3s-v1.23-brightgreen?style=for-the-badge&logo=kubernetes&logoColor=white)](https://k3s.io/)

</div>

---

## 📖 Overview
This directory contains kubernetes related infrastructure, such as a [__Helm__](https://helm.sh) registry and configuration managed by [__Flux__](https://fluxcd.io/).

---

## 📁 Directories
- [__`cluster`__](./cluster/): directory is the entrypoint to [__Flux__](https://fluxcd.io/).
- [__`helm`__](./helm/): directory is the entrypoint for a [__Helm__](https://helm.sh) registry deployed with [__GitHub Pages__](https://pages.github.com/).

---

## 🛠️ Build
### ⚙️ Components
My Kubernetes uses the following core components:

- [__mozilla/sops__](https://toolkit.fluxcd.io/guides/mozilla-sops/): Manages secrets for Kubernetes, Ansible and Terraform.
- [__kubernetes-sigs/external-dns__](https://github.com/kubernetes-sigs/external-dns): Automatically manages DNS records from my cluster in a cloud DNS provider.
- [__jetstack/cert-manager__](https://cert-manager.io/docs/): Creates SSL certificates for services in my Kubernetes cluster.
- [__kubernetes/ingress-nginx__](https://github.com/kubernetes/ingress-nginx/): Ingress controller to expose HTTP traffic to pods over DNS.

### 📦 Deployment
[![ArtifactHub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/simbleau&style=for-the-badge)](https://artifacthub.io/packages/search?user=simbleau)
[![Helm](https://img.shields.io/badge/Helm%203-https%3A%2F%2Fsimbleau.github.io%2Fhome--ops%2Fk8s%2Fhelm-0f1689?style=for-the-badge&logo=helm&logoColor=white)](https://simbleau.github.io/home-ops/k8s/helm)\
Applications I serve from my home, such as [__my website__](https://spencer.imbleau.com), are stored in a [__Helm 3__](https://helm.sh) registry, deployed with [__GitHub Pages__](https://pages.github.com/).

- **Registry URI**: `https://simbleau.github.io/home-ops/k8s/helm`

📕 _[__Click here__](./helm/) to learn more about my [__Helm__](https://helm.sh) registry._