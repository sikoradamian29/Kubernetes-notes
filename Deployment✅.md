#### A resource object that controls the [[Pods✅]] and ReplicaSets. It checks the health of the [[Pods✅]] and restarts the Pod's container if it terminates.

#### "You describe a _desired state_ in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new [[ReplicaSets✅]], or to remove existing Deployments and adopt all their resources with new Deployments."

#### "Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to Pods along with a lot of other useful features."

#### You can update the deployment when you need, so if you change an image in the yaml file and do kubectl apply -f then kubernetes creates new [ReplicaSet](ReplicaSets✅.md) and removes the old one. You can reverse this using [[Rollout✅]]

## Creating deployments using YAML file


```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

- kind - specifies the resource type to create by kubernetes
- metadata.name specifies the name of the deployment
- label - identifier by which you can filter your resources
- spec.replicas - specifies how many pods will be created
- spec.selector - defines how the created ReplicaSet finds which Pods to manage. In this case, you select a label that is defined in the Pod template (`app: nginx`)
- specs.template - specifies how the pods will be created
- spec.template.spec.containers - specifies the name, image and ports on which the app communicates

#### You can create the deployment (or any other resource) using
```bash
kubectl apply -f <filename.yaml>
```

#### You can scale the deployment (change the amount of replicas) using

```bash
kubectl scale --current-replicas=2 --replicas=3 deployment/nginx-deployment
```

#### You can remove the Deployment using

```bash
kubectl delete deployment nginx-deployment
```

