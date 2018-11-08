# Network

## Bridge

### Machine default

#### Create

```sh
docker-machine create \
  --engine-opt bip=10.0.0.1/16 \
  default
```

#### Config

```sh
jq ".HostOptions.EngineOptions.ArbitraryFlags[0] |= \"bip=10.0.0.1/16\"" ~/.docker/machine/machines/default/config.json | sponge ~/.docker/machine/machines/default/config.json
```

```sh
docker-machine provision
```
