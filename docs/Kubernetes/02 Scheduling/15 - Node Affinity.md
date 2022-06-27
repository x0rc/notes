# Node Affinity
*Node affinity is **a set of rules.** **It is used by the scheduler to decide where a pod can be placed in the cluster**.*


- apply label on a node
```bash
k apply label node node01 color=blue
```

- Set Node Affinity to the deployment to place the pods on `node01` only.

	-   Name: blue
	-   Replicas: 3
	-   Image: nginx
	-   NodeAffinity: requiredDuringSchedulingIgnoredDuringExecution
	-   Key: color
	-   value: blue
    
solution:
```
k create deployment blue2 --image=nginx --replicas=3 --dry-run=client -o yaml > deploy.yaml
---
edit deploy.yaml and under spec add

...
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: color
                operator: In
                values:
                - blue
...

```

- Create a new deployment named `red` with the `nginx` image and `2` replicas, and ensure it gets placed on the `controlplane` node only.

	- Use the label key - `node-role.kubernetes.io/master` - which is already set on the controlplane node. 
	-   Name: red
	-   Replicas: 2
	-   Image: nginx
	-   NodeAffinity: requiredDuringSchedulingIgnoredDuringExecution
	-   Key: node-role.kubernetes.io/master
	-   Use the right operator
	
solution:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: red
  name: red
spec:
  replicas: 2
  selector:
    matchLabels:
      app: red
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: red
    spec:
      containers:
      - image: nginx
        name: nginx
        resources: {}
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: node-role.kubernetes.io/master
                operator: Exists
status: {}
```