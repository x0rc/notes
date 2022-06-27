# Namespaces

- how to count the number of namespaces in a cluster
```bash
k get namespaces --noheaders | wc -l
```

- create a pod in a specified namespace
```bash
k run redis --image=redis -n <namespace>
```

- find on which namespace your pod is running
```bash
k get pods --all-namespaces | grep <YOUR POD NAME>
```	