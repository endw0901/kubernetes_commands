# DNSトラブルシューティング
- 14. Demo: DNS Troubleshooting(Optional) => 内容が？？？？？
- おそらく、フルドメインネームはnamecheapでホストされ、subdomainのみRoute53でpointするのではなくフルもRoute53をpointするためのやりかた？のよう

- kopsでcluster起動するにはDNSが正常に機能する必要がある
```
// hostを実行できるようにする(linux, mac)
sudo apt install bind9-host

// name serverが正常にセットされているかを確認 => Route53の設定がreturnされていればok
host -t NS xxxxxxxxxxxxxxxxxxx
```


### Route53(aws)でmainドメインをhostしたい場合(namecheapなどではなく)
- Hosted zoneName, Value
- namecheapのようなサイトを使うか、Route53でcreate host zoneする


```
// domainがnamecheapを指す=>そのnameserversがRoute53 valueのnameserverを指すようにすることも可能
whois xxxxx(domain name)
```

- Route53でnamecheapでcreate record setでk8のdomainのvalueを指定
