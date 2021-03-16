# Commands Cheatsheet

## Docker

```docker pull [image]```

```docker run -it --name [name] [image]```

```docker images```

```docker ps```

```docker tag [image] repo/image```

```docker push [image]```

## Azure Container Registry

```az login```

```az acr login --name [registry-name]```

```docker push [registry-name]```

# Azure Kubernetes Service

```az aks get-credentials --resource-group [name] --name [servicename]```

```kubectl get nodes```

```kubectl apply -f .\demodeployment.yaml```

```kubectl get pods -o wide```

```kubectl get service```

