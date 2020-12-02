# アプリ起動 on K8

- pod定義の作成 => image baseのコンテナをlaunch
- pod = k8上のアプリについての記述（複数コンテナ） local port numberを使い通信
- pod-xxxxx.ymlファイル

```
// pod作成
kubectl create -f k8s-demo/pod-xxxx.yml
```

### kubectlコマンド

```
kubectl get pod
kubectl describe pod
kubectl expose pod -port=444 -name=frontend

// exposed podをlocal machineへ
kubectl port-forward <pod> 8080


kubectl attach <podname> --command
kubectl label pods <pod> mylabel=xxxxx

// run a shell in a pod (for debug)
kubectl run -i --tty busybox --image=busybox --restart=Never --sh

```

### demo

```
// minikube running確認
kubectl get node

cd xxx
// pod生成
kubectl create -f first-app/helloworld.yml
kubectl get pod  

kubectl describe pod nodehelloworld.example.com

// local 8081でlisten => 3000へredirectを保証する
kubectl port-forward nodehelloworld.example.com 8081:3000

// open new shell
// 8081でresponse（3000へforwardされる
curl localhost:8081

```


```
// typeで、ダイレクトにk8上でport3000にアクセスできるということ
kubectl expose pod nodehelloworld.example.com --type=NodePort --name nodehelloworld-service

//minikubeの場合=> http://192.xxx.xx.100:31234のportが3000にport-forwardされるので、このreturnのipアドレスでサービスにアクセスできる
minikube service nodehelloworld-service --url
```





