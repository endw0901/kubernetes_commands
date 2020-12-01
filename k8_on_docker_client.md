# Docker上

## kubectl

```
// 1.docker-for-desktopを表示
kubectl get nodes

// 2.clusterを表示
kubectl config get-contexts

// 3.そのclusterにswitch
kubectl config use-context docker-for-desktop

// 4. run a pod => deployment created
kubectl run hello-kubernetes --image=k8.xxxxxxx/echoserver:1.4 ---port=8080

// 5.deployment(hello-kubernetes)をNodePortにexposeする
kubectl expose deployment hello-kubernetes --type=NodePort

// 6.serviceにアクセス => PORT(s) 8080:31453/TCPが表示される
kubectl get service hello-kubernetes

// 7.localhostのportにアクセス=>responseが返ってくる
localhost:31453
```
