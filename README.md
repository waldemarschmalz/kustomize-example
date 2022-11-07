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

Deploy Prometheus and Grafana:
```bash
kubectl apply -k monitoring/base/
```
#
Workaround when using persistent volumes mounted as `hostpath`:
The non-standard user UID: 65534 can't access it out of the box. 
So, "initContainers" will provide the user UID:65534 the required permission on the volume (volumeMounts).


_prometheus-deployment.yaml_:
```
initContainers:
- name: prometheus-data-permission-setup
  image: busybox
  command: [ "/bin/chmod","-R","777", "/data" ]
  volumeMounts:
    - name: prometheus-volume
      mountPath: /data
```

###

### TODOs

- credential management
- monitoring:
  - import Grafana dashboard in deployment