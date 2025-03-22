

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