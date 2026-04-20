# k8s-deployments

This directory contains the Kubernetes manifests for the current Home Assistant deployment.

## Files

- `homeassistant-namespace.yaml`: Creates the `homeassistant` namespace that isolates the workload and its namespaced resources.
- `homeassistant-pv.yaml`: Defines the persistent volume backed by NFS. This is where Home Assistant data is stored.
- `homeassistant-pvc.yaml`: Claims the persistent volume from inside the `homeassistant` namespace so the Pod can mount it.
- `homeassistant-app.yaml`: Defines the Home Assistant `Deployment`, including the container image, health checks, volume mount, and scheduling rules.
- `homeassistant-service.yaml`: Creates the internal `ClusterIP` Service that exposes Home Assistant on port `8123` inside the cluster.
- `ingressroute.yaml`: Defines the Traefik `IngressRoute` that maps `homeassistant-dev.lan` to the Home Assistant Service.
- `HA-setup-draft.md`: Draft article describing the current architecture, failover flow, and scheduling design.
- `LICENSE`: Repository license file.

## Apply Order

If you want to apply the manifests manually, use this order:

1. `homeassistant-namespace.yaml`
2. `homeassistant-pv.yaml`
3. `homeassistant-pvc.yaml`
4. `homeassistant-app.yaml`
5. `homeassistant-service.yaml`
6. `ingressroute.yaml`
