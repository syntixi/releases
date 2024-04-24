# Syntixi Release Repository

## Prerequisites

* **Kubernetes Cluster (1.24+)**: The cluster must be accessible from your machine.
* **Helm v3**: You may need to modify Helm command if you are using Helm v2. 

## Usage

### Add Syntixi Helm repository

1. Add chart repository: `helm repo add syntixi https://releases.syntixi.dev/`
2. Update repository: `helm repo update syntixi`
3. Search repo for releases: `helm search repo syntixi`
    * For development releases: `helm search repo syntixi --devel -l`

### Installation

Visit [installation guide](https://syntixi.dev/) for more information.