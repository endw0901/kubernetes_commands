# scaling pods

- stateless = appがstateを持たない = local filesを作成しない、local sessionsを保持しない

- Replication Controller => scalingを行う on k8 

```
kubectl get node

// replication controllerが2pods生成 
kubectl create -f xxxxx.yml(ReplicationControllerのymlファイル) 
kubectl get pods

// pod のimage pullまで待つ(describeは状況確認 
kubectl describe pod xxxxx( 

// ready状態　=> 水平scaleされた複数pod 
kubectl get pods
```

- この状態で、pod1つが止まると自動でrescale制御
- LB設定すれば複数podsにアクセスできるようになる　



```
// 1pod削除してcontrollerの挙動確認
kubectl delete pod xxxxxx

// deleted => new pod run
kubectl get pods
```


## Replication Controller起動後にscaleを増やす

```
kubectl scale --replicas=4 -f xxxxxxx(起動時のymlファイル)

// replication controllerの概要状況
kubectl get rc
```

- stateless podsであれば水平scaleが可能
- statefull podsは不可　


## controller削除

```
kubectl delete rc/xxxx(name) 
kubectl get pods

```
