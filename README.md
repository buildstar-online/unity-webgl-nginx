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
Demo site <a href="https://webgl-nginx.buildstar.online/">webgl-nginx.buildstar.online</a>
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

You will need either a Kubernetes cluster running [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) and the [Kubernetes Ingress-Nginx](https://github.com/kubernetes/ingress-nginx) controller, a virtual machine, or a bare-metal host.

If you do not have any of those available, the following resources can guide you through using Terraform to create one using various cloud providers.

- [Equinix Metal](https://github.com/buildstars-online/modules-equinix-tf-spot)
- [Azure](https://github.com/buildstars-online/azure-tf-starter)
- [Google Cloud Platform](https://github.com/buildstars-online/gcp-tf-starter)
- [Amazon Web Services](https://github.com/buildstars-online/modules-aws-ec2)


## k3s Quick Start

I advise using [K3s](https://k3s.io/) as it's very easy to deploy on Bare Metal and VMs as Single-Node cluster. This example shows a minimum-viable deployment.

1. Download and install K3s

    ```bash
    curl -sfL https://get.k3s.io | sh - 
    ```

2. Wait for node to be ready

    ```bash
    sudo k3s kubectl get node
    NAME   STATUS   ROLES                  AGE   VERSION
    vm0    Ready    control-plane,master   1m   v1.27.4+k3s1
    ```

3. Create the deployment and expose the service with a load-balancer

    ```bash
    sudo kubectl create -f https://raw.githubusercontent.com/buildstar-online/unity-webgl-nginx/main/kubernetes/default-k3s-deployment.yaml
    ```

4. Get the External-IP and port for the service

    ```bash
    sudo kubectl get svc -n webgl-nginx
    NAME                  TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)          AGE
    webgl-nginx-service   LoadBalancer   10.43.113.106   192.168.50.101   8080:30262/TCP   22m
    ```

4. Vist the site in your browser at `http://<external-ip>:8080/`

5. Cleanup

    ```bash
    /usr/local/bin/k3s-uninstall.sh
    ```

