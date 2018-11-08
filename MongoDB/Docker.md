# Docker

## Running

```sh
docker run -d \
  -h mongo \
  -v /opt/mongo/data/runtime/db:/data/db \
  -e MONGO_INITDB_ROOT_USERNAME=root \
  -e MONGO_INITDB_ROOT_PASSWORD='Pa$$w0rd!' \
  -p 27017:27017 \
  --name mongo \
  --restart always \
  mongo:4.1
```
