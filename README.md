# cluster-addons

## Description

This repo contains a list of helm charts that will all be deployed to a cluster.
It's deployed with an ArgoCD application-set that scans all the folders under the
/addons director for charts.


## Kustomize 

+ Place a values files that corresponds to the environment you want to deploy in 
such as values-dev.yaml in the directory that contains the helm chart.

+ Create a Kustomize overlay that matches the name of the enviroment such as overlays/dev.
Place a kustomization.yaml and application-set.yaml patch in the overlay/dev directory.

### Deployment with Kustomize

#### Dev:
```
kubectl apply -k overlays/dev
```

#### Prod:
```
kubectl apply -k base
```

## Rollback

It is recommended to make changes to the HEAD if you want to revert a change.  If you do need 
to roll back to a previous commit you would change the ApplicationSet section.

```
apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet
metadata:
  name: cluster-addons
  namespace: argocd
spec:
  generators:
  - git:
      repoURL: https://github.com/polinchw/cluster-addons.git
      revision: <previous-hash-or-tag-goes-here>
      directories:
      - path: addons/*
```