# K8s Playground
- Argocd Playground


## Pre-req

- Helm
```sh
    wget https://get.helm.sh/helm-v3.14.0-linux-amd64.tar.gz
    tar -zxvf helm-v3.14.0-linux-amd64.tar.gz linux-amd64/helm
    cd linux-amd64/helm
    mv helm /usr/local/bin/
```

- k3d
```sh
    wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```


## Start kind - Option 1
- Start your local cluster
```sh
 kind create cluster --name argocd
```


## Start k3d - Option 2

- Start your local cluster
```sh
    k3d cluster create argocd --image rancher/k3s:v1.31.1-k3s1
```