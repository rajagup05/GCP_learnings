
## Deploy ReplicaSet in Kubernetes Cluster

`Task`: **Create a ReplicaSet using `nginx` image with `latest` tag (ensure to specify as `nginx:latest`) and name it `nginx-replicaset`.
Apply labels: app as `nginx_app`, type as `front-end`.
Name the container `nginx-container`. Ensure the replica count is `4`.**

**Solution:** 

- created Replicaset using `nano replicaaset.yaml` command with below YAML: 

```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replicaset
  labels:
    app: nginx_app
    type: front-end
spec:
  replicas: 4
  selector:
    matchLabels:
      app: nginx
  template:
    metadata: 
      name: nginx-pod
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx-container
        image: nginx:latest 

```

- used $ `kubectl apply -f repliaset.yaml` to create a replicaset and below is the output:
```
replicaset.apps/nginx-replicaset created
```

- used $ `kubectl get replicaset` to see the created replicaset and below is the output:
```
NAME               DESIRED   CURRENT   READY   AGE
nginx-replicaset   4         4         4       14s 
```
