
## create a pod

YAML used: 

apiVersion: v1
kind: Pod
metadata: 
  name: my-pod
  labels:
    app: my-app
spec:
  containers:
  - name: my-container
    image: my-image:latest
    ports:
    - containerPort: 80
