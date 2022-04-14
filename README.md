# Kubernetes Configurations
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/simbleau)](https://artifacthub.io/packages/search?user=simbleau) \
All kubernetes configs here are for my personal home laboratory and self hosting.

## Useful Links
- Helm Repository: `https://simbleau.github.io/k8s`
- [ArtifactHub Packages](https://artifacthub.io/packages/search?user=simbleau)
- [DockerHub Repository](https://hub.docker.com/u/simbleau)
- [K8s YAML Validator](https://validkube.com/)

## Dependencies
- [Kubernetes](https://kubernetes.io/) cluster
- [Helm 3](https://helm.sh/) installed on the cluster

# Install
- From Repo (**Recommended**):
  - `helm repo add simbleau https://simbleau.github.io/k8s`
  - `helm repo update`
  - Deploy package
    - e.g. `helm install <release-name> simbleau/<chart-name> --version 0.1.0`
- From Package URL:
  - `helm install <release-name> https://simbleau.github.io/k8s/helm-chart-packages/website-0.1.0.tgz`

## Pushing Helm Charts
- `mkdir helm-chart-sources/<chart-name>`
- `helm create helm-chart-sources/<chart-name>`
- `helm lint helm-chart-sources/<chart-name>`
-  Consider [building a new package](#building-helm-packages)
-  Consider [updating the helm repository](#updating-helm-repository)

## Building Helm Packages
- `cd helm-chart-packages`
- `helm package ../helm-chart-sources/<chart-name>`

## Updating Helm Repository
- `helm repo index --url https://simbleau.github.io/k8s/ .`

# Troubleshooting
- View the template: `helm template helm-chart-sources/<chart-name>`

# License
This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
