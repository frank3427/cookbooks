# Issues

## DNS

> Error: forwarding ports: error upgrading connection: unable to upgrade connection: pod does not exist

Add current external ip and hostname to each node machine:

```sh
hostname -I
```

```sh
sudo sh -c 'echo -e "$(hostname -I | awk '\''{print $2}'\'')\t$(hostname -s)" >> /etc/hosts'
```

## Service Account

> Error: configmaps is forbidden: User "system:serviceaccount:kube-system:default" cannot list resource "configmaps" in API group "" in the namespace "kube-system"

```sh
kubectl create serviceaccount -n kube-system tiller
```

```sh
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
```

```sh
kubectl patch deploy -n kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'
```

```sh
helm init --service-account tiller --upgrade
```
