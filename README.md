# Kubernetes Orchestration Files
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/website)](https://artifacthub.io/packages/helm/simbleau/website)
All deployment files for my personal home laboratory and self hosting.

## Useful Links
- [Helm Repository](https://github.com/simbleau/k8s)
- [DockerHub Repository](https://hub.docker.com/u/simbleau)
- [K8s YAML Validator](https://validkube.com/)

# Deployment

## Dependencies
- [Helm](https://helm.sh/) (`curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash`)

## Updating Helm Repository
- `helm repo index --url https://simbleau.github.io/k8s/ .`

## Pushing Helm Charts
- `export CHART_NAME="test"`
- `mkdir helm-chart-sources/${CHART_NAME}`
- `helm create helm-chart-sources/${CHART_NAME}`
- `helm lint helm-chart-sources/${CHART_NAME}`
- `helm package helm-chart-sources/${CHART_NAME}`
-  Consider [updating the helm repository](#updating-helm-repository)

# License
This  project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
