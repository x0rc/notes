# Manual Scheduling

https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/

- example how to assign pod to a node(01)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  -  image: nginx
     name: nginx
  nodeName: node01
  ```
