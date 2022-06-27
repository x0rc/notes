# Deployments

- deployment example
```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-1
spec:
  replicas: 2
  selector:
    matchLabels:
      name: busybox-pod
  template:
    metadata:
      labels:
        name: busybox-pod
    spec:
      containers:
      - name: busybox-container
        image: busybox888
        command:
        - sh
        - "-c"
        - echo Hello Kubernetes! && sleep 3600
```

- creating deployment with kubectl
```
k create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=3
```

- To preview the object that would be applied to the cluster without really submitting it:
```bash
k create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=3 --dry-run=client -o yaml > deployment.yaml
```


![[Pasted image 20220627112244.png]]