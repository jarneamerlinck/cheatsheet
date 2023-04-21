---
topic: kubernetes_yaml
date: 2023/04/21
project: cheatsheet
type: note
---

# Kubernetes yaml
[Readme](../README.md)

## Deployment example

### With comments

```yaml
apiVersion: apps/v1  //diff for each component
kind: Deployment    //what
metadata:
  //name of deployment
  //used in selector Service
  //also used in pods
  name: nginx-deployment
  labels:
    app: nginx
spec: //configuraton for this yaml file
  replicas: 1 //number of pods
  //selectors are used to mach labels
  // key value (doesnt need to be app)
  selector:
    machtLabels:
      app: nginx
  //blueprints
  //config for pod
  template:
    metadata:
      labels:
        app:nginx
    spec:           // Blueprint
      containers:
      - name: nginx
        image: nginx:1.16
        ports:
        - containerPort: 80


```

### Without comments

```yaml
apiVersion: apps/v1 
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1 
  selector:
    machtLabels:
      app: nginx
  template:
    metadata:
      labels:
        app:nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.16
        ports:
        - containerPort: 80
```
## Deployment nodeport example

### With comments

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80          //service port
      targetPort: 8080  //container  port


```

### Without comments

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```