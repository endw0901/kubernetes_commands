# configmap

```
kubectl create configmap nginx-config --from-file=configmap/reverseproxy.conf 

// outputをyaml formatで
kubectl get configmap nginx-config -o yml
```
