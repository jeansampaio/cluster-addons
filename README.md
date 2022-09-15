# cluster-addons

## Description

This repo contains a list of helm charts that will all be deployed to a cluster.
It's deployed with an ArgoCD application-set that scans all the folders under the
/addons director for charts.


## Kustomize 

Place a values files that corresponds to the environment you want to deploy in 
such as values-dev.yaml in the directory that contains the helm chart.

Create a Kustomize overlay that matches the name of the enviroment such as overlays/dev.
Place a kustomization.yaml and application-set.yaml patch in the overlay/<env> directory.

### Deployment with Kustomize

#### Dev:
```
kubectl apply -k overlays/dev
```

#### Prod:
```
kubectl apply -k base
```
