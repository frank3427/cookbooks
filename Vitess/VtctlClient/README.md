# VtctlClient

##

```sh
export POD_NAME=$(kubectl get pods -n vitess -l 'app=vitess,component=vtctld' -o jsonpath='{.items[0].metadata.name}')
```

```sh
nohup kubectl port-forward --address 0.0.0.0 $POD_NAME 15999:15999 -n vitess &> /dev/null &
```
