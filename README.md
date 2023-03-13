# Syntixi Release Repository

## Prerequisites

* **Kubernetes Cluster (1.16+)**: The cluster must be accessible from your machine.
* **Helm v3**: You may need to modify Helm command if you are using Helm v2. 

## Usage

### Add Helm repo

1. Add chart repository: `helm repo add syntixi https://releases.syntixi.dev/`
2. Update repository: `helm repo update syntixi`
3. Search repo for releases: `helm search repo syntixi`
    * For development releases: `helm search repo syntixi --devel -l`

### Installation

```bash
$ kubectl create namespace syntixi

# Install the latest version
$ helm install syntixi --namespace syntixi --create-namespace syntixi/syntixi

# Install the specific version
$ helm install syntixi --namespace syntixi --create-namespace --version <chart_version> syntixi/syntixi 
```

### Upgrade

```bash
$ helm repo update syntixi
$ helm upgrade syntixi --namespace syntixi --version <chart_version> syntixi/syntixi
```

### Install CLI

Visit [release page](https://github.com/syntixi/releases/releases) to download CLI based on installed Syntixi version and your OS.

<details>
  <summary>MacOS</summary>

```bash
$ curl -fLO -o syntixi https://github.com/syntixi/releases/releases/download/$(curl https://raw.githubusercontent.com/syntixi/releases/master/stable.txt)/syntixi-cli-osx
$ chmod +x syntixi
$ mv syntixi /usr/local/bin/syntixi
```
</details>

<details>
  <summary>Linux</summary>

* AMD64
```bash
$ curl -fLO -o syntixi https://github.com/syntixi/releases/releases/download/$(curl https://raw.githubusercontent.com/syntixi/releases/master/stable.txt)/syntixi-cli-linux
$ chmod +x syntixi
$ mv syntixi /usr/local/bin/syntixi
```
</details>

<details>
  <summary>Others</summary>

Visit [release page](https://github.com/syntixi/releases/releases) to download CLI.
</details>