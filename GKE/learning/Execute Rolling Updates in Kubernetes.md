
## Execute Rolling Updates in Kubernetes

`Task:` **Execute a rolling update for this application, integrating the `nginx:1.19` image. The deployment is named `nginx-deployment`. Ensure all pods are operational post-update.**

- used $ `kubectl get deploy` to get the deployments name. Below was the output:

```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           2m26s
```
