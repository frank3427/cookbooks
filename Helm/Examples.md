# Examples

## Search

```sh
helm search stable/
```

## Repo

```sh
helm repo list
```

## Values

```sh
helm get values [name] --all
```

## Upgrade

```sh
helm get values [name] > values.yaml
```

```sh
helm upgrade [release] [chart] -f values.yaml
```

## Delete

```sh
helm list
```

```sh
helm del --purge [name]
```

```sh
kubectl delete pvc -l 'app=[name]'
```
