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
    kubectl kustomize --enable-helm bootstrap |  kubectl apply -f -
```

```sh
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    argocd admin initial-password -n argocd
```


## End


```sh
    k3d cluster delete argocd
```


## TODO File structure and workflow

- Create a helm chart for the bootstrap apps
- Redo bootstrap process to use kustomize to render my helm charts of bootstrap apps
- Referencing a specific values file per bootstrap app

https://kubectl.docs.kubernetes.io/references/kustomize/builtins/#_helmchartinflationgenerator_