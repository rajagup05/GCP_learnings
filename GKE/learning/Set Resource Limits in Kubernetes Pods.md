
## Set Resource Limits in Kubernetes Pods

`Task: `
**Create a pod named `httpd-pod` with a container named `httpd-container`. Use the `httpd` image with the `latest` tag (specify as `httpd:latest`). Set the following resource limits:**

` Requests: Memory: 15Mi, CPU: 100m ` \
`Limits: Memory: 20Mi, CPU: 100m`

- used `nano samplepod.yaml` and added below spec:

```
apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod
spec:
  containers:
  - name: httpd-container
    image: httpd:latest
    resources:
      limits:
        cpu: 100m
        memory: 20Mi
      requests:
        cpu: 100m
        memory: 15Mi 
```


