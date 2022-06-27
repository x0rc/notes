# PODs

- list pods
```bash
k get pods
```

- create a new pod with nginx image
```bash
k run nginx --image=nginx				# k run <name of pod> --image=<your image>
```

- check the image of a pod
```bash
k describe pod <pod name>
```

- check on which nodes are the pods placed
```bash
k get pods -o wide
```

The *READY* column in the output of the `k get pods` command indicates  **Running containers in POD/Total containers in POD**

- delete a pod
```bash
k delete pod <pod name>
```

- once created, we can edit the pod configuration with
```bash
k edit pod <pod name>
```