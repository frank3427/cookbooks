# Docker

## Running

```sh
docker run -d \
  -h airflow \
  -p 8080:8080 \
  --name airflow \
  --restart always \
  puckel/docker-airflow:latest
```
