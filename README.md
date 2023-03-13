# Syntixi Release Repository

## Prerequisites

* **Kubernetes Cluster (1.20+)**: The cluster must be accessible from your machine.
* **Helm v3**: You may need to modify Helm command if you are using Helm v2. 

## Usage

### Add Syntixi Helm repository

1. Add chart repository: `helm repo add syntixi https://releases.syntixi.dev/`
2. Update repository: `helm repo update syntixi`
3. Search repo for releases: `helm search repo syntixi`
    * For development releases: `helm search repo syntixi --devel -l`

### Install Syntixi

```bash
# Install the latest version
$ helm install syntixi --namespace syntixi --create-namespace syntixi/syntixi

# Install the specific version
$ helm install syntixi --namespace syntixi --create-namespace --version <chart_version> syntixi/syntixi 
```

If your Kubernetes environment doesn't [persistence volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
yet, please set `storage.persistence.enabled` to `false` 


```bash
$ helm install syntixi --namespace syntixi --create-namespace \
    --set storage.persistence.enabled=false syntixi/syntixi
```

### Upgrade

```bash
$ helm repo update syntixi
$ helm upgrade syntixi --namespace syntixi --version <chart_version> syntixi/syntixi
```

### Install Syntixi CLI

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

## Hello World!

```bash
# A javascript one-liner that prints "hello world"
$ curl https://raw.githubusercontent.com/syntixi/examples/master/environments/nodejs/hello.js > hello.js

# Upload your function code
$ syntixi bundle create --name hello-bundle --code hello.js

# Create the function with the bundle just created
$ syntixi function create --name hello \
    --image node:16-alpine3.11 \
    --bundle hello-bundle \
    --entry "node hello.js" 

# Your function is about to start running within a pod.
$ kubectl get pod -l functionName=hello

# Run the function.  This takes about 100msec the first time.
$ syntixi function test --name hello
Hello World
```