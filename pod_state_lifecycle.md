# pod state lifecycle

- Pod Status => kubectl get podsで見れる
- Pod condition => kubectl describe pod (PODNAME)
- Container State

## pod lifecycle

- init container => main container (別々) 
- post start hook
- pre stop hook

```
watch -n1 kubectl get pods

// 別画面
kubectl create -f xxx.yaml

// podの中身確認
kubectl exec -it xxxxxxI(podname) -- cat /xxxx
```
