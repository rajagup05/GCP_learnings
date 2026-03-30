
## Setup Kubernetes Namespaces and PODs

`Task`: **Create a namespace named dev and deploy a POD within it. Name the pod dev-nginx-pod and use the nginx image with the latest tag. Ensure to specify the tag as nginx:latest**.


- used `$ kubectl create namespace dev` to create namespace.
- used `nano pod.yaml` with below spec:

```
apiVersion: v1
kind: Pod
metadata:
  name: dev-nginx-pod
spec:
  containers: 
  - name: dev-nginx-container
    image: nginx:latest
```

- 
