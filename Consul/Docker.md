# Docker

## Running

```sh
docker run -d \
  -h consul \
  -e CONSUL_BIND_INTERFACE=eth0 \
  -p 8500:8500 \
  --name consul \
  --restart always \
  consul:1.4.3
```
