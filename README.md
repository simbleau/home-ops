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

# Deploying
- From Repo (**Recommended**):
  - `helm repo add simbleau https://simbleau.github.io/k8s`
  - `helm repo update`
  - Deploy package
    - e.g. `helm install my-website simbleau/website --version 0.1.0`
- From Package URL:
  - `helm install test-web https://simbleau.github.io/k8s/helm-chart-packages/website-0.1.0.tgz`

## Pushing Helm Charts
- `export CHART_NAME="test"`
- `mkdir helm-chart-sources/${CHART_NAME}`
- `helm create helm-chart-sources/${CHART_NAME}`
- `helm lint helm-chart-sources/${CHART_NAME}`
-  Consider [building a new package](#building-helm-packages)
-  Consider [updating the helm repository](#updating-helm-repository)

## Building Helm Packages
- `export CHART_NAME="test"`
- `cd helm-chart-packages`
- `helm package ../helm-chart-sources/${CHART_NAME}`

## Updating Helm Repository
- `helm repo index --url https://simbleau.github.io/k8s/ .`

# License
This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
