# jenkins.local-keycloak-poc
Just a simple repo to test keycloak for jenkins

Its just a poc for replacing the current accounts system from jenkins with a different external maintained solution.
---

# Cluster setup
```shell
k3d cluster create --config k3d-cluster.yml
``` 

## Create namespace and install helmchart
```shell
kubectl apply -f keycloak/namespace.yml
```
```shell
helm repo add codecentric https://codecentric.github.io/helm-charts
```
```shell
helm install keycloak codecentric/keycloak --namespace keycloak -f keycloak/helm-values.yml
```

## Hosts file entries
```
127.0.0.1 jenkins.local
127.0.0.1 keycloak.jenkins.local
127.0.0.1 admin.keycloak.jenkins.local
```