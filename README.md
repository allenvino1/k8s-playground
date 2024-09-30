# K8s Playground
- Argocd Playground


## Bug
- need to re-run twice as the argocd CRds as not yet initialized. 
https://github.com/kubernetes-sigs/kustomize/issues/4354


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


## Start Argocd Bootstrap

- Install Argo and install other applications on the fly.
```sh
    cd argocd/ 
    kubectl kustomize --enable-helm bootstrap |  kubectl apply -f -
```

```sh
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    argocd admin initial-password -n argocd
```


## Cleanup


```sh
    $ k3d cluster delete argocd
    or
    $ kind delete cluster --name argocd
```


## TODO File structure and workflow

- Create a helm chart for the bootstrap apps [DONE]
- Redo bootstrap process to use kustomize to render my helm charts of bootstrap apps [DONE]
- Referencing a specific values file per bootstrap app [DONE]

https://kubectl.docs.kubernetes.io/references/kustomize/builtins/#_helmchartinflationgenerator_