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

