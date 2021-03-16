# Commands Cheatsheet

## Basic

### Docker

```docker pull [image]```

```docker run -it --name [name] [image]```

```docker images```

```docker ps```

```docker tag [image] repo/image```

```docker push [image]```

### Azure Container Registry

```az login```

```az acr login --name [registry-name]```

```docker push [registry-name]```

### Azure Kubernetes Service

```az aks get-credentials --resource-group [name] --name [servicename]```

```kubectl get nodes```

```kubectl apply -f .\demodeployment.yaml```

```kubectl get pods -o wide```

```kubectl get service```

* * *

## All Useful Commands

```kubectl create -f ./letskubedeploy.yml *NodePort (local) or LoadBalancer*```

```kubectl apply -f ./letskubedeploy.yml```

```kubectl get pods```

```kubectl get svc```

```kubectl describe pod letskube-deployment-6985756df5-ssrlg```

```kubectl delete deployment letskube-deployment```

```kubectl delete service letskube-service```

```kubectl delete -f ./letskubedeploy.yml```

```az login```

```az account show --output table```

```az account list-locations```

```az group create -n letskuberg -l ukwest```

```az acr --help```

```az acr create --help```

```az acr create -n letskubeacr1 -g letskuberg  -l ukwest --sku basic```

```az acr login -n letskubeacr1```

```az acr list -o table *letskubeacr1.azurecr.io*```

```docker tag letskube:local letskubeacr1.azurecr.io/letskube:v1```

```docker image list```

```docker push letskubeacr1.azurecr.io/letskube:v1```

```az acr repository list -n letskubeacr1 -o table```

### create service principal

```az ad sp create-for-rbac --skip-assignment```

```$acrId = az acr show --name letskubeacr1 --resource-group letskuberg --query "id" --output tsv```

```az role assignment create --assignee "2b222285-9b22-47e2-8b8d-8c807f2772bf" --role Reader --scope $acrId```

###  create AKS cluster

```az aks create --name letskubeakscluster --resource-group letskuberg --node-count 1 --generate-ssh-keys --service-principal "2b222285-9b22-47e2-8b8d-8c807f2772bf" --client-secret "6e8c8fcb-b232-48ab-9733-c487b5116216" --location northeurope ```

###  repoint local to AKS

```cat C:\Users\owlfa\.kube\config | more```

```az aks get-credentials --name letskubeakscluster --resource-group letskuberg```

```cat C:\Users\owlfa\.kube\config | sls "letskubeakscluster"```

```kubectl get nodes```

```kubectl apply -f ./letskubedeploy.yml```

```kubectl get service --watch```

###  scale

```az aks scale --name letskubeakscluster --resource-group letskuberg --node-count 3```

```kubectl get nodes / pods```

```kubectl get deployment```

```kubectl scale --replicas=5 deployment/letskube-deployment```

### update

```docker build . -t letskubeacr1.azurecr.io/letskube:v2```

```docker push letskubeacr1.azurecr.io/letskube:v2```

```kubectl set image deployment letskube-deployment letskube=letskubeacr1.azurecr.io/letskube:v2```

### change to local context

```kubectl config current-context```

```kubectl config use-context docker-for-desktop```