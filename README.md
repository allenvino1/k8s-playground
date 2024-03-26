# K8s Playground
- Argocd Playground



## Pre-req

- Helm
```sh
    wget https://get.helm.sh/helm-v3.14.0-linux-amd64.tar.gz
```


## Start

- Start your local cluster
```sh
    k3d cluster create argocd --agents 1 --image rancher/k3s:v1.23.16-k3s1
```

- Install Argo and install other applications on the fly.
```sh
    cd argocd/
    kubectl kustomize --enable-helm bootstrap/ |  kubectl apply -f -
```

```sh
    k3d cluster delete argocd
```