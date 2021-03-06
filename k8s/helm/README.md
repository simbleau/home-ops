<div align="center">

<img src="https://simpleicons.org/icons/helm.svg" width="144px" height="144px"/>

# Helm Registry
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)
[![Helm](https://img.shields.io/badge/Helm%203-0f1689?style=for-the-badge&logo=helm&logoColor=white)](https://helm.sh)

---
## `https://simbleau.github.io/home-ops/k8s/helm`
---

</div>

## 📖 Overview
This directory a [__Helm 3__](https://helm.sh) registry, deployed with [__GitHub Pages__](https://pages.github.com/).

---

## 📁 Directories
- [__`charts`__](./charts/): Helm charts as source.
- [__`packages`__](./packages/): Helm charts as installable packages.

---

## 📦 Deployment
[![ArtifactHub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/simbleau&style=for-the-badge)](https://artifacthub.io/packages/search?user=simbleau)

GitHub Pages allows us to configure this repository as a static site, which easily translates to a Helm registry. ArtifactHub provides us a front-end to our registry which is searchable and can be verified.

---

## 🧰 Development
[![DockerHub](https://img.shields.io/badge/DockerHub-simbleau-2496ed?style=for-the-badge&logo=docker&logoColor=white)](https://hub.docker.com/u/simbleau)

In general, all programs and images I own are uploaded and verified on DockerHub. From these images, I develop Helm charts which are packages for my cluster.

### Testing Dependencies
- [Kubernetes](https://kubernetes.io/) cluster or [minikube](https://minikube.sigs.k8s.io/)
- [Helm 3](https://helm.sh/) installed on the cluster
- Repository:
  - `helm repo add simbleau https://simbleau.github.io/home-ops/k8s/helm`
  - `helm repo update`

### Creating Helm Charts
- Create: `mkdir k8s/helm/charts/<chart-name>`
- Init: `helm create k8s/helm/charts/<chart-name>`

### Testing Deployment
- From source: `helm install <release-name> k8s/helm/charts/website`
- From package: `helm install <release-name> k8s/helm/packages/website-0.1.0.tgz`
- From registry: `helm install <release-name> simbleau/<chart-name> --version 0.1.0`

### Building Helm Packages
- `cd k8s/helm/packages`
- `helm package ../charts/<chart-name>`

### Updating the Helm Registry
- `cd k8s/helm`
- `helm repo index --url https://simbleau.github.io/home-ops/k8s/helm/ .`

### Troubleshooting
- Validation: `helm lint k8s/helm/charts/<chart-name>`
- View template: `helm template k8s/helm/charts/<chart-name>`