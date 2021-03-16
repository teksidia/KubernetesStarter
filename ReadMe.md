# Basic Starter - Kubernetes using AKS / Visual Studio 2019

Useful courses:

- [Microsoft Azure for .NET Developers - Building Secure Services and Applications (Orchestrating Microservices with Azure Kubernetes Service)](
https://app.pluralsight.com/course-player?clipId=a48a74be-f9ee-4d4d-ad10-ba9af61c20b0)

- [Azure Kubernetes Service (AKS) – The Big Picture](https://app.pluralsight.com/library/courses/azure-container-service-big-picture/table-of-contents)

## Prerequisites (for Windows) ##

* Visual Studio > 2019
* Docker for Windows (inc kubectl)
* .NET Core SDK >= 3.1 
* Azure CLI
* Recommended - VS Code (with Docker extension)
* Azure CLI tools

## Basic Steps ##

### Develop microservices in VS (using Docker Compose)

1. Create microservices e.g. web API / UI
2. "Add Container Orchestration" in VS for each project
3. Edit image names in docker-compose.yml to match registry/repo naming convention
4. Edit docker-compose project properties (e.g. set startup project)
5. Run and test locally using Docker Compose VS runner

### Push images to ACR

1. Check images names match registry convention (see step 3 in previous)
1. Create release build images (latest)
2. ```az login```
3. ```az acr login --name [registry-name]```
4. ```docker push [registry-name]```

### Create AKS deployment via manifest

1. ```az aks get-credentials --resource-group [name] --name [servicename]```
2. ```kubectl apply -f .\demodeployment.yaml```
3. Wait for service to come up (`kubectl get service --watch`) and browse to service's public IP

See also [Commands Cheatsheet](https://github.com/teksidia/KubernetesStarter/blob/master/CommandsCheatsheet.md)
