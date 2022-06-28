# Monitor Cluster components

- deploying metrics server to monitor PODs & Nodes

```shell
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```


- You might face with this problem:
![[Pasted image 20220628092251.png]]

- fix: 	download the components.yaml and add --kubelet-insecure-tls  
```yaml
template:  
metadata:  
labels:  
k8s-app: metrics-server  
spec:  
containers:  
- args:  
- --cert-dir=/tmp  
- --secure-port=4443  
- --kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname  
- --kubelet-use-node-status-port  
- --metric-resolution=15s  
- --kubelet-insecure-tls  
image: k8s.gcr.io/metrics-server/metrics-server:v0.5.2
```

**Usage of `--kubelet-insecure-tls` is expected in clusters that don't provide proper certificates to Kubelet. Such clusters should not be used in production**

- The top command allows you to see the resource consumption for nodes or pods.
![[Pasted image 20220628092647.png]]