# cluster-addons

## Description

This repo contains a list of helm charts that will all be deployed to a cluster.
It's deployed with an ArgoCD application-set that scans all the folders under the
/addons director for charts.

## Deployment


### Dev:
```
kubectl apply -k overlays/dev
```

### Prod:
```
kubectl apply -k base
```
