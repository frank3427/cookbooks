# Docker

## Running

```sh
docker run -d \
  -h redis \
  -v /opt/redis/data:/data \
  -p 6379:6379 \
  --name redis \
  --restart always \
  redis:latest redis-server --appendonly yes
```
