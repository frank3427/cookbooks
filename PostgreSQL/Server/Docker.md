# Docker

## Running

```sh
docker run -d \
  -h postgres \
  -e POSTGRES_PASSWORD=postgres \
  -p 5432:5432 \
  --name postgres \
  --restart always \
  postgres:11.2-alpine
```
