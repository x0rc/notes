# Static PODs

- managed directly by kubelet daemon on a specific node
- static Pods running on a node are visible on the API server, but cannot be controlled from there.
-   Unlike Pods that are managed by the control plane (for example, a [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)); instead, the kubelet watches each static Pod (and restarts it if it fails).
-   The name of static pod is suffixed with the name of the node
-   The `spec` of a static Pod cannot refer to other API objects (e.g., [ServiceAccount](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/), [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/), [Secret](https://kubernetes.io/docs/concepts/configuration/secret/), etc).

The static pod definition files path can be found in the config files of the kubelet daemon on a specific node.

```
# -e shows all the current processes, -f shows full format listing, search for --config, which shows the config files for the kubelet

ps -ef | grep kubelet

# result looks something like this  
--config=/var/lib/kubelet/config.yaml

# search for static inside the config file  
grep -i static /var/lib/kubelet/config.yaml

# result is like this   
staticPodPath: /etc/kubernetes/manifests

# Run this command on the node where the kubelet is running
systemctl restart kubelet
```

- this is an example of static pods running in a node
![[Pasted image 20220627152356.png]]
Remember? The name of static pod is suffixed with the name of the node.

- How to create a static pod?

![[Pasted image 20220627153917.png]]

- Move it to /etc/kubernetes/manifests

![[Pasted image 20220627154133.png]]

![[Pasted image 20220627154149.png]]