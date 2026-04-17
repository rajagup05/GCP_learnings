
## Schedule Cronjobs in Kubernetes

`Task:` 

**Create a cronjob named `devops`. \
Set Its schedule to something like `*/4 * * * *`. You can set any schedule for now. \
Name the container `cron-devops`. \
Utilize the nginx image with latest tag (specify as `nginx:latest`). \
Execute the dummy command `echo Welcome to xfusioncorp!`. \
Ensure the restart policy is `OnFailure`.** 

- Created `cron.yaml` using nano:
```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: devops
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: cron-devops
            image: nginx:latest
            command:
            - echo "welcome to xfusioncorp!"
          restartPolicy: OnFailure
```
- used $ `kubectl apply -f cron.yaml` to create this conJob and below is the output:
```
cronjob.batch/devops created
```

- used $ `kubectl get jobs` to check if jobs are running:
```
NAME              STATUS    COMPLETIONS   DURATION   AGE
devops-29602969   Running   0/1           65s        65s
devops-29602970   Running   0/1           5s         5s
```

