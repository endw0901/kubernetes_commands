# 便利なkubectlコマンド

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

### more

```

kubectl attach nodehelloworld.example.com

// running containerの/app配下フォルダ
kubectl exec nodehelloworld.example.com -- ls /app

// running containerにファイル作成
kubectl exec nodehelloworld.example.com -- touch /app/text.txt

// Endpoints , NodePort(static)
kubectl get service
kubectl describe serice nodehelloworld-service

// new pod with new containerでshell起動 
kubectl run -i --tty busybox --image=busybox --restart=Never -- sh

// shell内で、Endpointsにtelnet => getでレスポンス
telnet xxx.xx.x.x 3000
GET /

```
