# Syntixi Release Repository

## Prerequisites

* **Kubernetes Cluster (1.16+)**: The cluster must be accessible from your machine.
* **Helm v3**: You may need to modify Helm command if you are using Helm v2. 

## Usage

1. Add this repo to Helm: `helm repo add syntixi-charts https://charts.syntixi.dev/`
2. Search repo to get the latest version list: `helm search repo syntixi-charts`
3. Install one of the charts, for example `syntixi`:
    
```bash
$ kubectl create namespace syntixi
$ helm install --namespace syntixi --name-template syntixi \
    syntixi-charts/syntixi
```
