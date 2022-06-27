# DaemonSets

-   DaemonSet ensures that all (or some, matching a node selector) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. Deleting a DaemonSet will clean up the Pods it created.
-   DaemonSet implements a single instance of a pod on all (or filtered subset of) worker node(s).

- Some typical uses of a DaemonSet are:
	-   Running a cluster storage daemon on every node.
	-   Running a logs collection daemon on every node.
	-   Running a node monitoring daemon on every node.

---

- Task: Deploy a **DaemonSet** for `FluentD` Logging.
Use the given specifications.
	-   Name: elasticsearch
	-   Namespace: kube-system
	-   Image: k8s.gcr.io/fluentd-elasticsearch:1.20
	
	
- Solution: An easy way to create a DaemonSet is to first generate a YAML file for a Deployment with the command `kubectl create deployment elasticsearch --image=k8s.gcr.io/fluentd-elasticsearch:1.20 -n kube-system --dry-run=client -o yaml > fluentd.yaml`. Next, remove the replicas, strategy and status fields from the YAML file using a text editor. Also, change the kind from `Deployment` to `DaemonSet`. Finally, create the **Daemonset** by running: `kubectl apply -f fluentd.yaml`


```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  creationTimestamp: null
  labels:
    app: elasticsearch
  name: elasticsearch
  namespace: kube-system
spec:
  selector:
    matchLabels:
      app: elasticsearch
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: elasticsearch
    spec:
      containers:
      - image: k8s.gcr.io/fluentd-elasticsearch:1.20
        name: fluentd-elasticsearch
        resources: {}
```