<div align="center">

<img src="https://simpleicons.org/icons/kubernetes.svg" width="144px" height="144px"/>

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
- [__`cluster`__](./cluster/): directory is the entrypoint to Flux.
- [__`helm`__](./helm/): directory is the entrypoint for a Helm registry deployed with GitHub Pages.

---

## 🛠️ Build
### ⚙️ Components
My Kubernetes cluster uses the following core components:

- [__projectcalico/calico__](https://github.com/projectcalico/calico): Internal Kubernetes networking plugin.
- [__mozilla/sops__](https://toolkit.fluxcd.io/guides/mozilla-sops/): Manages secrets for Kubernetes, Ansible and Terraform.
- [__jetstack/cert-manager__](https://cert-manager.io/docs/): Creates SSL certificates for services in my Kubernetes cluster.
- [__kubernetes/ingress-nginx__](https://github.com/kubernetes/ingress-nginx/): Ingress controller to expose HTTP traffic to pods over DNS.
- [__kubernetes-sigs/external-dns__](https://github.com/kubernetes-sigs/external-dns): Automatically manages DNS records from my cluster in a cloud DNS provider.
- [__k8s_gateway__](https://github.com/ori-edge/k8s_gateway): CoreDNS plugin to resolve all types of external Kubernetes resources

### 📦 Deployment
[![Helm](https://img.shields.io/badge/Helm%203-0f1689?style=for-the-badge&logo=helm&logoColor=white)](https://helm.sh)
[![ArtifactHub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/simbleau&style=for-the-badge)](https://artifacthub.io/packages/search?user=simbleau)

Applications I serve from my home, such as [__my website__](https://spencer.imbleau.com), are stored in a Helm 3 registry, deployed with GitHub Pages.

- **Registry URI**: `https://simbleau.github.io/home-ops/k8s/helm`

📕 _[__Click here__](./helm/) to learn more about my Helm registry._

### 🌐 DNS
[![cloudfare](https://img.shields.io/badge/Cloudflare-Enabled-F38020?style=for-the-badge&logo=Cloudflare&logoColor=white)](https://uptimerobot.com)

My DNS is composed of three entities:
- [__Cloudfare__](https://cloudfare.com): A Cloud DNS provider which only talks to my ingress controller and hides my home IP.
- [__external-dns__](https://github.com/kubernetes-sigs/external-dns): External DNS operator which syncs records to Cloudfare.
- [__k8s_gateway__](https://github.com/ori-edge/k8s_gateway): Internal DNS operator serving my internal network.

#### Ingress Controller
- Over WAN, I have forwarded ports `80` and `443` to the load balancer IP of my ingress controller that's running in my Kubernetes cluster. Cloudfare works as a proxy to hide my WAN IP and acts as a firewall. When not on my home network, all the traffic coming into my ingress controller on port `80` and `443` comes from Cloudflare. I block all IPs not originating from the [Cloudflares list of IP ranges](https://www.cloudflare.com/ips/).

#### Internal DNS
- [k8s_gateway](https://github.com/ori-edge/k8s_gateway) has direct access to my clusters ingress records and serves DNS for them in my internal network. `k8s_gateway` is only listening on `127.0.0.1` on port `53`.

#### External DNS
- [external-dns](https://github.com/kubernetes-sigs/external-dns) is deployed in my cluster and configured to sync DNS records to [Cloudflare](https://www.cloudflare.com/). The only ingresses `external-dns` looks at to gather DNS records to put in `Cloudflare` are ones that I explicitly set an annotation of `external-dns/is-public: "true"`

📕 _[__Click here__](./terraform/) to learn about how I manage Cloudflare with Terraform._

### Dynamic DNS
- My home IP can change at any given time and in order to keep my WAN IP address up to date on Cloudflare, I have a [CronJob](./cluster/apps/networking/cloudflare-ddns) in my cluster, this periodically checks and updates the `A` record `ipv4.domain.tld`.