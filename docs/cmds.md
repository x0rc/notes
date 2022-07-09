# x0rchive


```bash
```

| command | time | date | description |
| ------- | ---- | ---- | ----------- |
| sudo snap install kontena-lens --classic | 17:52:14 | 07/09/22 | visualise your k8s cluster |
| kubectl run nginx --image=nginx | 20:33:41 | 07/09/22 | create pod |
| k get pods -o wide | 20:35:53 | 07/09/22 | wide info |
| k run redis --image=redis --dry-run=client -o yaml > redis.yaml | 20:40:28 | 07/09/22 | creates manifest file |
| k create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=3 --dry-run=client -o yaml > deployment.yaml | 22:05:19 | 07/09/22 | no desc provided |
| k run redis --image=redis -l tier=db | 22:16:17 | 07/09/22 | add label / imperative cmd |
| kubectl expose pod redis --port=6379 --name redis-service | 22:20:57 | 07/09/22 | expose service |
