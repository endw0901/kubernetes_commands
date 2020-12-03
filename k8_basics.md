# basics
- kubelet => 起動
- kube-proxy => iptablesにnode上のpodの情報を渡す
- iptables => firewallの機能　=> load balancerがiptableとやりとり(AWS ELB)
- ELBがINTERNETからアクセスできる  

- INTERNET => ELB => iptables => pod on Docker => container on pod
