# Unity WebGL on Kubernetes

This repo contains the resources and workflows required to build and deploy a Unity3D WebGL project using [GameCI](https://game.ci/), [Kubernetes](https://kubernetes.io/) and [ArgoCD](https://argo-cd.readthedocs.io/en/stable/).

<p align="center">
<img width="600" alt="Screenshot 2023-05-10 at 08 17 15" src="https://github.com/buildstars-online/unity-webgl-nginx/assets/84841307/2a05bfc3-b665-4df6-a28d-8a01c06da4c8">
</p>

<p align="center">
<img width="600" alt="Screenshot 2023-05-10 at 08 25 04" src="https://github.com/buildstars-online/unity-webgl-nginx/assets/84841307/8fdf7ecf-425e-458f-8550-caf84789d426">
</p>

## Prerequisites

A Kubernetes cluster running [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) and the [Kubernetes Ingress-Nginx](https://github.com/kubernetes/ingress-nginx) controller. 
If you do not have a clister or single-node available, the following resources can guide you through using Terraform to create one using various cloud providers.

- [Equinix Metal](https://github.com/buildstars-online/modules-equinix-tf-spot)
- [Azure](https://github.com/buildstars-online/azure-tf-starter)
- [Google Cloud Platform](https://github.com/buildstars-online/gcp-tf-starter)
- [Amazon Web Services](https://github.com/buildstars-online/modules-aws-ec2)

For Bare Meatl and Single-Node installations, I advise using [K3s](https://k3s.io/). For a batteries-included installation, my preference is to set it up via [smol-k8s-lab](https://github.com/small-hack/smol-k8s-lab) which installs ArgoCD, Nginx, CertManager, and Metallb.
