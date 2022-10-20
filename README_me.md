# Kustomize Example

# Setup kubectl

If no remote kubernetes available, start your own:
```
minikube start --nodes 2 -p multinode-demo
```

To see whats going on, use:
```
minikube dashboard -p multinode-demo
```

once you are finished, stop your local kubernetes with
```
minikube stop -p multinode-demo
```

Setup some useful aliases:

```
alias kn='kubectl config set-context --current --namespace '
alias kgp='kubectl get pods'
alias k='kubectl'
```

# Start the services

Postgres
```
k apply -k postgres/overlays/dev
```

```
k apply -k postgres/overlays/dev
```


# Setup port forward
Setup port forward to reach a service
```
k port-forward service/keycloak-http 8080:80
```

