# volume

- mountしたvolumeにアクセス

```
kubectl exec xxxxxxxx -i -t -- bash
ls -ahl /myvol/
echo 'test' > /myvol/myvol.txt

```

## delete volume

```
// detach
kubectl delete -f volumes/xxxxxxxxxx.yml

// delete
aws ec2 delete-volume --volume-id vol-xxxxxxxxxxxxx
```

## auto-provisioning

- https://kubernetes.io/docs/concepts/storage/persistent-volumes/
