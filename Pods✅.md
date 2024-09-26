#### _Pods_ are the smallest deployable units of computing that you can create and manage in Kubernetes.

#### A _Pod_ is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers.

#### You can create a pod this way:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: nginx-container
    image: nginx:latest
    ports:
    - containerPort: 80
  - name: redis-container
    image: redis:latest
    ports:
    - containerPort: 6379
```

```bash
kubectl apply -f <filename.yaml>
```
