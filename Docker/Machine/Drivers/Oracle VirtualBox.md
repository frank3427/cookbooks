# Oracle VirtualBox

## Create

```sh
docker-machine --debug create \
  --driver virtualbox \
  --virtualbox-cpu-count 4 \
  --virtualbox-disk-size 40000 \
  --virtualbox-hostonly-cidr '10.100.1.1/24' \
  --virtualbox-memory 8192 \
  [name]
```
