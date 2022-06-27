# ReplicaSets

**ReplicaSets ensures that the desired number of PODs always run**

- how many replicasets exist on the system?
```bash
k get replicasets
```

- ReplicaSet example
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: replicaset-1
spec:
  replicas: 2
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: nginx
        image: nginx
```

- we can edit the replicaset config by
```bash
k edit replicaset <replicaset name>
```

*If we already have running pods from the replicaSet the changes will not take effect unless we delete(recreate) the pods.*

- we can scale replicasets by editing the manifest or over terminal with:
```bash
k scale replicasets <name of the replicaSet> --replicas=<NUMBER OF REPLICAS>
```