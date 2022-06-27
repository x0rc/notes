# Resource Limits

- We have a pod which requires 1 CPU and the pod is crushing.

![[Pasted image 20220627142544.png]]

- Node specs:

![[Pasted image 20220627142803.png]]

The node doesnt meet the requirements for the pod.

---


- The status `OOMKilled` indicates that it is failing because the pod ran out of memory. Identify the memory limit set on the POD.

![[Pasted image 20220627143122.png]]

---

- Container resources example

```yaml
---
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
  - name: log-aggregator
    image: images.my-company.example/log-aggregator:v6
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
```
