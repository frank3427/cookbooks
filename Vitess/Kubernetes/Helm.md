# Helm

## Namespace

```sh
kubectl create ns vitess
```

```sh
kubens vitess
```

## Dependencies

- [etcd Operator](https://github.com/coreos/etcd-operator)

## Creating

```sh
kubectl create secret generic vitess-db-password --from-literal=password='vitess123'
```

```sh
git clone https://github.com/vitessio/vitess.git vitess && cd "$_"
```

```sh
cat << EOF | helm install helm/vitess -n vitess -f -
topology:
  cells:
    - name: zone1
      keyspaces:
        - name: vitess
          shards:
            - name: '0'
              tablets:
                - type: replica
                  vttablet:
                    replicas: 1
      mysqlProtocol:
        enabled: true
        authType: secret
        username: vitess
        passwordSecret: vitess-db-password
      etcd:
        replicas: 3
      vtctld:
        replicas: 1
      vtgate:
        replicas: 3

vttablet:
  dataVolumeClaimSpec:
    storageClassName: nfs-slow
EOF
```

### Port Forward

```sh
export POD_NAME=$(kubectl get pod -l 'app=vitess,component=vtgate' -o jsonpath='{.items[0].metadata.name}')
```

```sh
nohup kubectl port-forward --address 0.0.0.0 $POD_NAME 3306:3306 &> /dev/null &
```

#### Stop

```sh
kill "$(lsof -nPi tcp:3306 | grep LISTEN | awk '{print $2}')"
```
