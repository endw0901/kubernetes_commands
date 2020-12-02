# Kops

- linux, macで動く
- Windowsはvirtual boxが必要（Hyper-Vも？)

```
mkdir ubuntu
cd ubuntu

// vagrant file作成
vagrant init ubuntu/xenial64

// virtualboxをubuntuセットアップして起動
vagrant up

// logoin for mac,linux
vagrant ssh
// ログインwindows
vagrant ssh-config

```



- Windows UsersはIdentityFileにprivate_keyのアドレス表示がある

```
// puttygen puttyでprivate keyでubuntuにアクセスするか、open sshライブラリをinstallしてログイン 
puttygen putty
```

## linux kops

```
wget https://github.com/kubernetes/kops/releases/download/v1.4.1/kops-linux-amd64
chmod +x kops-linux-amd64
sudo mv kops-linux-amd64 /user/local/bin

// AWSダウンロードに必要(pips)
sudo apt-get install python-pip
sudo pip install awscli

//確認
aws
```

- AWS IAMで、programmatic access onlyのuser作成
- userをgroupに追加、AdministratorAccess付与（全部できる)
- access key, secret access key取得

```
// access key、secret access key入力
aws configure

// credentialsファイル生成を確認
ls -ahl ~/.aws/
```

### S3
- s3 で新規bucket生成(kops-state-xxxxxx)、regionはclusterのregion
- cloundping.infoサイトで自分の場所から最も低latencyのregion確認が可能

### Route53：subdomain
- kopsはsubdomainをmanagesするので、事前にRoute53で作成

- Domain registration(.tkなど無料のものを)
- domainすでにあり => domain management
- Host Zone作成（費用かかる) => domain Name, 
- valueがsub-domain
- サイト：namecheapなどでadvanced DNSでNSレコード作成

### kubectl install
```
// kubernetesとkubectl versionをそろえること
// version確認　
kubectl version

wget https://storage.googleapis.com/kubernetes-release/release/v1.4.3/bin/linux/amd64/kubectl

// kopsと同じ場所に移動
sudo mv kubectl /usr/local/bin/
sudo chmod +x /user/local/bin/kubectl
kubectl
sudo mv /usr/local/bin/kops-linux-amd64 /usr/local/bin/kops
```

### ssh key create
-  cluster loginに使う

```
ssh-keygen -f .ssh/id_rsa

```

## cluster

```
// full DNS namesを指定してcluster作成 (plan表示のみ)
kops create cluster --name=kubernetes.xxxx(domain) --state=s3://kops-state-xxx  --zones=eu-west-1a --node-count=2 --node-size=t2.micro --master-size=t2.micro --dns-zone=kubernetes.xxxxx(domain)

// 修正
kops edit cluster kubernetes.xxxx(domain) --state=s3://kops-state-xxx

// launch cluster
kops update cluster kubernetes.xxx(domain) --yes --state=s3://kops-state-xxx　

// clusterログイン用のcertificateとpasswordが格納されている
cat ~/.kube/config

// masterと2nodes表示される
kubectl get node

// kubectl run (start a pod)
// echoserver imageはdocker上(8080)
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
kubectl expose deployment hello-minikube --type=NodePort --port=8080

// service確認
kubectl get services
```

- EC2 instance確認
- EC2 auto-scaling group確認(master, node)
- description => security group => inbound rule, outbound rule (firewall block有無を確認) 
- add new ruleで起動したservice(hello-minikube)のports 8080:30032/TCPの30032を追加（custome TCP / TCP / 30032 / My IP => save
- instance => ipv4 public ipのport xx.xx.xx.xxx:30032でアクセス=> serviceのレスポンス確認


## cluster delete

```
kops delete cluster kubernetes.xx(domain) --state=s3:/xxxxx --yes

```
