# Tanzu Platform Capabilities

This repo is a collection of field provided custom capabilties to add additional functionality to tanzu Platform. These are not officially suppoprted by Tanzu. 


## Capabilities

[Deployments](./deployments/) - this enabled the `deployments.apps.v1` api and the `services.v1` core k8s apis 

## Install

Installing this repo will give access to all of the capabilties defined here.

1. add the package repo to the project

```bash
tanzu project use <your-proj>
export KUBECONFIG=~/.config/tanzu/kube/config
kubectl apply -f capabilities-repo/package-repository.yml
```

2. add the package repo to the cluster group(this is only needed until the next release of TP, instructions will be updated after the release)

```bash
tanzu ops clustergroup use <your-cg>
export KUBECONFIG=~/.config/tanzu/kube/config
kubectl apply -f capabilities-repo/package-repository.yml
```

## Contributing

### Add a new capability

To add a new capability follow the instructions below:

1. create a new directory for the capability
2. Add a README to the directory
3. create a package directory in the folder `mycapability-package`
4. init a carvel package in the directory
    ```bash
    cd mycapability-package
    kctrl package init
    ```
5. add the capability contents to the package
6. release the package
    ```bash
    kctrl package release --version 1.0.0 --repo-output ../../capabilities-repo
    ```
7. publish a new version of the repo
    ```bash
    cd ../../capabilities-repo
    kctrl package repo release -v 1.0.0
    ```