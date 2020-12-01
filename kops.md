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
- userにAdministratorAccess付与（全部できる)





