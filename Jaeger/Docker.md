# Docker

## Running

### Collector

```sh
docker run -d \
  -h jaeger-collector \
  -e SPAN_STORAGE_TYPE=elasticsearch \
  -p 9411:9411 \
  -p 14267:14267 \
  -p 14268:14268 \
  --name jaeger-collector \
  --restart always \
  jaegertracing/jaeger-collector:latest --es.server-urls=http://elasticsearch:9200
```

### Agent

```sh
docker run -d \
  -h jaeger-agent \
  -p 5775:5775/udp \
  -p 5778:5778 \
  -p 6831:6831/udp \
  -p 6832:6832/udp \
  --name jaeger-agent \
  --restart always \
  jaegertracing/jaeger-agent:latest --collector.host-port=jaeger-collector:14267
```

### Query

```sh
docker run -d \
  -h jaeger-query \
  -e SPAN_STORAGE_TYPE=elasticsearch \
  -p 16686:16686 \
  --name jaeger-query \
  --restart always \
  jaegertracing/jaeger-query:latest --es.server-urls=http://elasticsearch:9200 --log-level=debug
```
