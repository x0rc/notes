# Commands & Arguments
- commands in k8s manifest
```yaml
...
spec:
  containers:
  - name: ubuntu
    image: ubuntu
    command:
      - "sleep"
      - "5000"
...
```

- commands in Dockerfile
```yaml
ENTRYPOINT ["python", "app.py"]
```

The `ENTRYPOINT` in the Dockerfile is overridden by the `command` in the pod definition.

```yaml
FROM python:3.6-alpine

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]

CMD ["--color", "red"]
```

vs.

```yaml
apiVersion: v1 
kind: Pod 
metadata:
  name: webapp-green
  labels:
      name: webapp-green 
spec:
  containers:
  - name: simple-webapp
    image: kodekloud/webapp-color
    command: ["--color","green"]
```

Since the entrypoint is overridden in the pod definition, the command that will be run is just `--color green`

- arguments

```yaml
...
spec:
  containers:
  - name: simple-webapp
    image: kodekloud/webapp-color
    command: ["python", "app.py"]
    args: ["--color", "pink"]
...
```

`python app.py --color pink` will be executed.

- creating a pod with args
```yaml
apiVersion: v1 
kind: Pod 
metadata:
  name: webapp-green
  labels:
      name: webapp-green 
spec:
  containers:
  - name: simple-webapp
    image: kodekloud/webapp-color
    args: ["--color", "green"]
```