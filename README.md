# Example Incidents

## Stress

### Components used

1. [docker-stress docker hub](https://hub.docker.com/r/polinux/stress)
2. [docker-stress Github](https://github.com/pozgo/docker-stress)

### Usage

1. Create an OpenShift cluster
2. Set `KUBECONFIG` env variable
3. Create a deployment:
   1. Exhaust allocated memory
      1. `oc apply -k stress/overlays/memory-alloc/`
   2. Exhaust tmpfs filesystem memory
      1. `oc apply -k stress/overlays/memory-emptydir/`
4. Monitor your cluster's resource utilization
   1. `oc adm top node`
   2. `oc -n stress adm top pod`
   3. `oc -n stress get pods`