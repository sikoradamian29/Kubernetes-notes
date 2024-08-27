#### Kubernetes can check if a container is still alive through `liveness probes`. You can specify a liveness probe for each container in the [pod](Pods)'s specification. Kubernetes can probe the container using one of three mechanisms:

- An `HTTP GET` probe performs an HTTP GET request on the container's IP address, a port and path you specify. If the probe receives a response and the response code doesn’t represent an error **(in other words, if the HTTP response code is 2xx or 3xx)**, the probe is considered successful. If the server returns an error response code or if it doesn’t respond at all, the probe is considered a failure and the container will be restarted as a result.
- A `TCP Socket` probe tries to open a TCP connection to the specified port of the container. If the connection is established successfully, the probe is successful. Otherwise, the container is restarted.
- An `Exec` probe executes an arbitrary command inside the container and checks the command’s exit status code. If the status code is 0, the probe is successful. All other probes are considered as failure.

#### How to create a livenessProbe:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: kubia-liveness
spec:
  containers:
  - image: knrt10/kubia-unhealthy
    name: kubia
    livenessProbe:
      httpGet:
        path: /
        port: 8080
```

#### Here kubernetes will periodically send a GET request to the application in the container to check if it's available (if it doesn't return 2xx nor 3xx code it will restart the container)

