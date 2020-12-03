# deploy

- Replica SetはReplication Controllerよりfiltering条件を細かい条件文でしていできる(イコール文だけでなく)

- appのstateを定義 => k8がappが指定のstateになっていることを保証する　



```
// deployment生成
kubectl create -f deployment/xxxxx.yml
kubectl get deployments 

```

- desired replica数、current replica数・・が表示される

```
// k8が自動でrsを生成してくれる
kubectl get rs
kubectl get pods
kubectl get pods --show-labels

// roll out成功したか確認 
kubectl rollout status deployment/xxxxx-deployment
``` 

## docker hub のimage versionの変更 => roll back

```
kubectl expose deployment xxxx-deployment --type=NodePort
kubectl get service
kubects describe service xxxx-deployment
minikube service xxx-deployment --url http://xxx.xxx.xxx:31969
curl http://xxx.xx.xxx.::31969

// tag number2に変える
kubectl set image deployment/xxx-deployment k8s-demo=xxxx/k8s-dmo:2
kubectl rollout status deployment/xxxx-deployment
curl http:///xx.xxx:13969

// 変更前imageのpodがterminateされ、変更後imageのpodがrunしていることを確認
kubectl get pods

// rollout history確認
kubectl rollout history deployment/xxx-deployment

// roll back
kubectl rollout undo deployment/xxxx-deployment
```

## edit

- --to-revision=xで指定したrevisionへ

```
kubectl edit deployment/xxx-deployment
kubectl set image deployment/xxx-deployment k8s-demo=xxxx/k8s-demo:2
kubectl rollout history deployment/xxx-deployment

// historyのrevision番号を指定してroll back
kubectl rollout undo deployment/xxx-deployment --to-revision=3

```
