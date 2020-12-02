# loadbalancer

-- hostnameをLBにpointすることでインターネット上でhostのサービスをアクセス可能とする

```
// pod生成
kubectl create -f first-app/helloworld.yml
// service生成
kubectl create -f first-app/helloworld-service.yml
```

- ELB作成
```
aws iam create-service-linked-role --aws-service-name "elasticloadbalancing.amazonaws.com"  
```

- EC2 => load balancers => port80=> instance port32162へpointしているのを確認=> nodeはportへ連携

-- Route53でhostnameをloadbalancerにdns解決レコード作成 => hostnameへアクセスすると、LB経由でinstance podへ連携、サービスのレスポンスを得れる





