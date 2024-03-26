# K8s Playground
- Argocd Playground



## Start

- Start your local cluster
```sh
    k3d cluster create argocd --agents 1 --image rancher/k3s:v1.23.16-k3s1
```


- Install Argo and install other applications on the fly.
```sh
    kubectl kustomize --enable-helm bootstrap/ |  kubectl apply -f -
```




