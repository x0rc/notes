# Cluster Maintenance

## OS Upgrades

We have a cluster with 2 nodes.
![[Pasted image 20220626231405.png]]

To check how many applications are hosted on the cluster:
![[Pasted image 20220626231627.png]]

Which nodes are the applications hosted on?
![[Pasted image 20220626231747.png]]


We need to take `node01` out for maintenance. Empty the node of all applications and mark it unschedulable.
![[Pasted image 20220626231913.png]]

What nodes are the apps on now?
![[Pasted image 20220626232022.png]]

** Applying Patches... **

The maintenance tasks have been completed. Configure the node `node01` to be schedulable again.
![[Pasted image 20220626232153.png]]

However, there are no pods scheduled on `node01`. *Only when new pods are created they will be scheduled.* The pods are placed on the `controlplane` node, because it does not have any taints.
![[Pasted image 20220626232621.png]]

If there is a pod which is not part of a replicaset, we cannot  drain node.
![[Pasted image 20220626232946.png]]
A forceful drain of the node will delete any pod that is not part of a replicaset.

To mark a node as  `unschedulable` so that no new pods are scheduled on this node we can:
![[Pasted image 20220626233616.png]]


--- 

## Takeaways


Taints and Tolerations – Concepts
```
Taints and tolerations are a mechanism that allows you to ensure that pods are not placed on inappropriate nodes. Taints are added to nodes, while tolerations are defined in the pod specification. When you taint a node, it will repel all the pods except those that have a toleration for that taint. A node can have one or many taints associated with it.

For example, most Kubernetes distributions will automatically taint the master nodes so that one of the pods that manages the control plane is scheduled onto them and not any other data plane pods deployed by users. This ensures that the master nodes are dedicated to run control plane pods.

A taint can produce three possible effects:

NoSchedule

The Kubernetes scheduler will only allow scheduling pods that have tolerations for the tainted nodes.

PreferNoSchedule

The Kubernetes scheduler will try to avoid scheduling pods that don’t have tolerations for the tainted nodes.

NoExecute

Kubernetes will evict the running pods from the nodes if the pods don’t have tolerations for the tainted nodes.
```

Commands used:
```bash
kubectl cordon my-node                                                # Mark my-node as unschedulable
kubectl drain my-node                                                 # Drain my-node in preparation for maintenance
kubectl uncordon my-node                                              # Mark my-node as schedulable
```