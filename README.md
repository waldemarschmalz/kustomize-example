### Apply K8s manifests

This is a simple kustomize example for running keycloak with a postgres db.
It is not production ready!


Deploy Postgres statefulset:
```bash
kubectl apply -k postgres/overlays/dev/
```

Deploy Keycloak statefulset with two instances:
```bash
kubectl apply -k keycloak/overlays/dev/
```
###

### TODOs

- credential management
- use kustomize patching
- ...