# healthcheck

- ymlファイルにlivenessProbeを入れ、path, portなどを設定

```
kubectl create -f deployment/helloworld-healthcheck.yml
kubectl get pods

// 設定したhealthcheck状態が表示される(Liveness)
kubectl describe pod xxxxx


```

- どれか一つのpodがおかしくなったとかわかる。サービスは継続しつつ 

```
kubectl edit deployment/helloworld-deployment
```


## readinessProbes

- livenessProbes : コンテナが起動しているかどうかのcheck => fail => restart
- readinessProbes : requestを受けれる状態かどうかをcheck => fail => Pod's IP をremove => service requestを受けれなくする(restartしない)
- 通常は両方とも必要
 
