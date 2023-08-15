<h1 align=center>
WebGL on Kubernetes w/ ArgoCD
</h1>

<p align="center">
  <img width="64" src="https://icons-for-free.com/iconfiles/png/512/kubernetes-1331550890056502145.png">
  <img width="64" src="https://icons-for-free.com/iconfiles/png/512/argocd-1331550886883580947.png">
  <img width="64" src="https://cdn4.iconfinder.com/data/icons/logos-brands-5/24/unity-1024.png">
<p>

<p align=center>
Resources and Workflows to build & deploy Unity3D WebGL builds using <br>
  <a href="https://game.ci/">GameCI</a>, <a href="https://kubernetes.io/">Kubernetes</a> and <a href="https://argo-cd.readthedocs.io/en/stable/">ArgoCD</a>.
<br>
<br>
Demo site <a href="http://webgl-nginx.buildstar.online/">HERE</a>
</p>
<br>
<p align="center">
<img width="600" alt="Screenshot 2023-05-10 at 08 17 15" src="https://github.com/buildstars-online/unity-webgl-nginx/assets/84841307/2a05bfc3-b665-4df6-a28d-8a01c06da4c8"> <br>
<img width="600" alt="Screenshot 2023-05-10 at 08 25 04" src="https://github.com/buildstars-online/unity-webgl-nginx/assets/84841307/8fdf7ecf-425e-458f-8550-caf84789d426">
</p>

## Contents

Workflows:
- [Activate License](https://github.com/buildstar-online/unity-webgl-nginx/blob/main/.github/workflows/activation.yml)
- [Build a Unity WebGL artifact using a custom image](https://github.com/buildstar-online/unity-webgl-nginx/blob/main/.github/workflows/build-unity-artifact.yml)

<p align="center">
<img width="325" alt="Screenshot 2023-08-15 at 14 47 34" src="https://github.com/buildstar-online/unity-webgl-nginx/assets/84841307/c46a73cf-1d23-45e6-bc6c-53af9a6c7095">
</p>

- [Build a Nginx Container](https://github.com/buildstar-online/unity-webgl-nginx/blob/main/.github/workflows/build-docker-image.yaml)

<p align="center">
<img width="325" alt="Screenshot 2023-08-15 at 14 47 49" src="https://github.com/buildstar-online/unity-webgl-nginx/assets/84841307/fb9fc851-d508-4779-afc8-66b28a95cfe1">
</p>

Templates:
- [Kubernetes Deployment](https://github.com/buildstar-online/unity-webgl-nginx/blob/main/kubernetes/basic-deployment.yaml)
- [ArgoCD Application](https://github.com/buildstar-online/unity-webgl-nginx/blob/main/argo-app.yaml)
- [Nginx Dockerfile & config](https://github.com/buildstar-online/unity-webgl-nginx/tree/main/docker)


## Requirements

A Kubernetes cluster running [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) and the [Kubernetes Ingress-Nginx](https://github.com/kubernetes/ingress-nginx) controller. 
If you do not have a cluster or single-node available, the following resources can guide you through using Terraform to create one using various cloud providers.

- [Equinix Metal](https://github.com/buildstars-online/modules-equinix-tf-spot)
- [Azure](https://github.com/buildstars-online/azure-tf-starter)
- [Google Cloud Platform](https://github.com/buildstars-online/gcp-tf-starter)
- [Amazon Web Services](https://github.com/buildstars-online/modules-aws-ec2)

For Bare Meatl and Single-Node installations, I advise using [K3s](https://k3s.io/). For a batteries-included installation, my preference is to set it up via [smol-k8s-lab](https://github.com/small-hack/smol-k8s-lab) which installs ArgoCD, Nginx, CertManager, and Metallb.
