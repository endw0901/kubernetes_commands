
# label

- labelはresourceへのtag
- 複数設定可能
- 正規表現で Label Selectors

- 例：tag the node => nodeSelectorをpod configurationにadd

```

kubectl get nodes
kubectl get nodes --show-labels
kubectl create -f deployment/helloworld-nodeselector.yml
kubectl get deployments
kubectl describe pod xxxxx
  
kubectl label nodes minikube xxxxxxx
kubectl get nodes --show-labels
kubectl get pods
kubectl describe pod xx

  
```
