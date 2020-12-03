# service

- podsはdynamicにscaleされるので直接アクセスしない。service経由（ＬＢ）とする
- serviceがpodのendpoint: ClusterIP(内部からのみ。デフォルト）か、NodePort(外部からもアクセス可能)かload balance

- 1.ClusterIP
- 2.NodePort
- 3.LoadBalancer (ELB on AWS) : nodeport経由で外部トラフィックをroute

- virtualIP(or ports)または、ExternalNameが提供するDNS names

```
// minikube 起動状態
kubectl get node
kubectl create -f first-app/hello.yml
kubectl get pods
kubectl describe pod nodehelloworld.example.com(pod name)

kubectl create -f first-app/helloworld-nodeport-service.yml
minikube service helloworld-service --url http://xx.xxx.xx:31001
curl http:/xxx.xx.x:31001

// svc = service
kubectl describe svc helloworld-service
// summary情報
kubectl get svc
```

- 再作成するとvirtual IPは変わるがstatic portは同じ
```
kubectl delete svc helloworld-service


kubectl create -f first-app/helloworld-nodeport-service.ymd
kubectl describe svc helloworld-service

```
