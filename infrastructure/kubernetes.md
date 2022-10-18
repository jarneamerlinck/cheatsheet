# Kubernetes
[Readme](../README.md)

## Overview
- [play with k8s](https://labs.play-with-k8s.com/) can help to learn docker
- All installers are in the installer repo
### Aliases
- alias k='kubectl'
- alias kn='kubectl config set-context --current --namespace='
- alias h='helm'

### Terminology
| What       | Meaning                                                                              |
| ---------- | :----------------------------------------------------------------------------------- |
| Nodes      | Hosts that run k8s                                                                   |
| Pods       | Running containers                                                                   |
| Namespace  | Namespace to collect all services/pods that are used for the same project            |
| Replicaset | replicaset is the number of pods that need to be running a one time                  |
| Deployment | deployment is an config for an image that includes exposed ports and the replica set |
| Ingress    | This manages external acces to the pods. Also does ssl certs and load balancing      |


## Commands


| What                                       | Command                                           |
| ------------------------------------------ | :------------------------------------------------ |
| See all                                    | ```k get all```                                   |
| See nodes                                  | ```k get nodes```                                 |
| See pods                                   | ```k get pods```                                  |
| See services                               | ```k get services```                              |
| See replicaset                             | ```k get replicaset```                            |
| See deployments                            | ```k get deployments```                           |
| See nodes                                  | ```k get nodes```                                 |
| See logs by appname                        | ```k logs -l app=name i```                        |
| Describe pod                               | ```k describe podName```                          |
|                                            |
| Attach pod                                 | ```k exec --stdin --tty podN_name -- /bin/bash``` |
| create namespace                           | ```k create namespace name```                     |
| Deploy yaml file                           | ```k apply -f fileName.yaml```                    |
| Edit deployment                            | ```k edit deployment name```                      |
| remove stuff by label                      | ```k delete pods,services -l app=myLabel```       |
| remove stuff by deployment (preferred way) | ```k delete deployment deploymentName```          |

### Arguments

#### Arguments for ```kubectl get```

| Arguments       | Command                                           |
| --------------- | :------------------------------------------------ |
| All name spaces | ```--all-namespaces```                            |
| Ps output       | ```-o wide```                                     |
| Json output     | ```-o json```                                     |
| Template output | ```-o what_to_get --template={{.status.phase}}``` |

## Applications for k8s

### datree
Datree is used to keep your deployment files safe.

| What             | Command                               |
| ---------------- | :------------------------------------ |
| Login            | ```datree config set token <token>``` |
| Check deployment | ```datree test deployment.yml```      |


### Helm
- [hub](https://artifacthub.io/)

| What                 | Command                                                                                                                           |
| -------------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| Add repo             | ```h repo add repo_name repo_url```                                                                                               |
| Seach for chart      | ```h seach repo name```                                                                                                           |
| Install chart        | ```h install project_name repoName/project``` <br> ```h install project_name repoName/project --values=project_name_values.yml``` |
| See install charts   | ```h ls --namespace namespace```                                                                                                  |
| Upgrade chart values | ```h upgrade project_name repo/project --values```                                                                                |




### Traefik
Is used as ingress controller or reverse proxy
