# Taints & Tolerations

- check if there are any taints on a node
```bash
k describe node <NODE NAME> | grep Taints
```

- create a taint on `node01` with key of `spray`, value of `mortein` and effect of `NoSchedule`:
```bash
k taint nodes node01 spray=mortein:NoSchedule
```

- create a pod named `bee` with the `nginx` image, which has a toleration set to the taint `mortein`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: bee
  name: bee
spec:
  containers:
  - image: nginx
    name: bee
    resources: {}
  tolerations:
  - key: spray
    value: mortein
    effect: NoSchedule
    operator: Equal
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```

`bee` pod was scheduled on node `node01` despite the taint.

- taint/untaint
![[Pasted image 20220627130748.png]]

https://medium.com/kubernetes-tutorials/making-sense-of-taints-and-tolerations-in-kubernetes-446e75010f4e