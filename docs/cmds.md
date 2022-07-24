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
| k run pod custom-nginx --image=nginx --port=8080 | 22:24:05 | 07/09/22 | exposing container port 8080 |
| docker buildx build --build-context init=init/ . --build-context iwshop=../src/iwshop.repo/ -f iwshop.repo/Dockerfile -t test:v1.0 | 19:22:27 | 07/10/22 | build docker images w/ multiple build contexts |
| tf init -backend-config="access_key=REDACTED" -backend-config="secret_key=REDACTED" -backend-config="region=us-east-1" | 09:24:59 | 07/20/22 | get tf state |
| k exec deploy/iwapi -- printenv | 13:41:52 | 07/21/22 | prints env vars from a pod |
| k set image po redis redis=redis | 11:57:58 | 07/24/22 | update pod image |
| xargs -a a.txt -n1 -I{} sh -c 'echo {} \| base64 -d' | 17:10:02 | 07/24/22 | will base64 decode every line from a txt file |
| find . -type f \| grep '\.json'  | 17:58:24 | 07/24/22 | lists only .json files |
| find . -type f \| grep '\.js$'  | 17:59:19 | 07/24/22 | lists only .js files |
| docker image inspect 406912119862.dkr.ecr.us-east-1.amazonaws.com/iwjwt \| gron \| grep PATH | 18:11:27 | 07/24/22 | the day I met GRON |
| docker image inspect 406912119862.dkr.ecr.us-east-1.amazonaws.com/iwjwt \| gron \| grep PATH \| gron -u | 18:11:44 | 07/24/22 | gron reverse |
