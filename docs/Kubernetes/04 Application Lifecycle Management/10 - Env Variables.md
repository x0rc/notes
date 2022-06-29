# Env Variables

- creating a pod with with Label name webappcolor & env APP_COLOR=green
```bash
k run webapp-color --image=kodekloud/webapp-color --labels="name=webapp-color" --env="APP_COLOR=green"
```

- creating a `ConfigMap` for a pod with given data: APP_COLOR=darkblue
```bash
k create configmap webapp-config-map --from-literal=APP_COLOR=darkblue
```

- updating env variable on a POD to use newly created ConfigMap

```yaml
...
spec:
  containers:
  - envFrom:
    - configMapRef:
         name: webapp-config-map
...
```