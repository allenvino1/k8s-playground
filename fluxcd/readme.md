# Setup 

kubectl create ns flux-system

# Install Operator
```
helm install flux-operator oci://ghcr.io/controlplaneio-fluxcd/charts/flux-operator \
  --namespace flux-system
```


# Create a fluxcd instance
kubectl apply -f flux-instance.yaml


# Debugging
- curl -s https://fluxcd.io/install.sh | sudo FLUX_VERSION=2.0.0 bash
- flux get all -A --status-selector ready=false
