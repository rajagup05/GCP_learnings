
## Execute Rolling Updates in Kubernetes

`Task:` **Execute a rolling update for this application, integrating the `nginx:1.19` image. The deployment is named `nginx-deployment`. Ensure all pods are operational post-update.**

- used $ `kubectl get deploy` to get the deployments name. Below was the output:

```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           2m26s
```

- used $ `kubectl get pods` to get the running pods

```
NAME                               READY   STATUS    RESTARTS   AGE
nginx-deployment-fc677cbc9-2d5w6   1/1     Running   0          6m36s
nginx-deployment-fc677cbc9-7pqjd   1/1     Running   0          6m36s
nginx-deployment-fc677cbc9-k4x2p   1/1     Running   0          6m36s
```

- used $ `kubectl describe pods nginx-deployment-fc677cbc9-2d5w6` => described one pod to get container name
 
- used $ `kubectl set image deployment/nginx-deployment nginx-container=nginx:1.19` to update image name for `nginx-container` container for this deployment and below is the output:
```
deployment.apps/nginx-deployment image updated
```


**OR**

we wcan also use $ `kubectl edit deploy nginx-deployment`  to edit the image and save to reapply the updated config for this deployment
