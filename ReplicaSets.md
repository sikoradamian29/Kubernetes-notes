#### A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. As such, it is often used to guarantee the availability of a specified number of identical Pods.

#### When you create a deployment it creates a [ReplicaSet](ReplicaSets) that manages specified amount of [[Pods]], but when you scale it, it creates a new ReplicaSet and gradually moves the resources from old ReplicaSet to the new one.

##### If the deployment named mysql's current size is 2, scale mysql to 3
```sh
kubectl scale --current-replicas=2 --replicas=3 deployment/mysql
```

#### You can create a ReplicaSet without a deployment, but it's not recommended, unless you require custom update orchestration or don't require updates at all.
