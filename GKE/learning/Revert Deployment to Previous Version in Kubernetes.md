
## Revert Deployment to Previous Version in Kubernetes

`Task:` There exists a deployment named `nginx-deployment`; initiate a rollback to the previous revision.

- used $ `kubectl get deployments` to list existing deployments:
``` 
Output: 
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           8m38s
```

- used $ `kubectl rollout --help` to seek help on rollback and below is the information I got:
```
Manage the rollout of one or many resources.
        
 Valid resource types include:

  *  deployments
  *  daemonsets
  *  statefulsets
Examples:
  # Rollback to the previous deployment
  kubectl rollout undo deployment/abc
  
  # Check the rollout status of a daemonset
  kubectl rollout status daemonset/foo
  
  # Restart a deployment
  kubectl rollout restart deployment/abc
  
  # Restart deployments with the 'app=nginx' label
  kubectl rollout restart deployment --selector=app=nginx

Available Commands:
  history       View rollout history
  pause         Mark the provided resource as paused
  restart       Restart a resource
  resume        Resume a paused resource
  status        Show the status of the rollout
  undo          Undo a previous rollout

```

- used $ `kubectl rollout undo deployment/nginx-deployment` and below is the output:
```
deployment.apps/nginx-deployment rolled back
```

- used $ `kubectl rollout status deployment/nginx-deployment ` to see the status of the deployment and below is the output:
```
deployment "nginx-deployment" successfully rolled out
```

