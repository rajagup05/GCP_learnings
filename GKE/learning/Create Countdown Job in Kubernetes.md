
## Create Countdown Job in Kubernetes

`Task:` **Create a job named `countdown-datacenter`.
The spec template should be named `countdown-datacenter` (under metadata), and the container should be named `container-countdown-datacenter`
Utilize image debian with latest tag (ensure to specify as `debian:latest`), and set the restart policy to `Never`.
Execute the command `sleep 5`** 

- used $ `nano job.yaml` to create a `job.yaml` and below is the YAML:

```
apiVersion: batch/v1
kind: Job
metadata:
  name: countdown-datacenter
spec:
  template:
    metadata:
      name: countdown-datacenter
    spec:
      containers:
      - name: container-countdown-datacenter
        image: debian:latest
        command: [sleep 5]
      restartPolicy: Never 
```
