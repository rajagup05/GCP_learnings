
## Deploy Applications with Kubernetes Deployments

`Task`: **Create a deployment named `nginx` to deploy the application `nginx` using the image `nginx:latest` (ensure to specify the tag)**

- used `nano deploy.yaml` and added below configuration/YAML:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      name: nginx
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx:latest
        name: nginx

```

- used `kubectl apply -f deploy.yaml` and deployment was created sucessfully. 
