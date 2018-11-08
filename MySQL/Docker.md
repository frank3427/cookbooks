# Docker

## Volume

```sh
docker volume create mysql-data
```

## Running

### 5.x

```sh
docker run -d \
  -h mysql \
  -e MYSQL_ROOT_PASSWORD=root \
  -v mysql-data:/var/lib/mysql \
  -p 3306:3306 \
  --name mysql \
  --restart always \
  mysql:5.7
```

### 8.x

```sh
docker run -d \
  -h mysql \
  -e MYSQL_ROOT_PASSWORD=root \
  -p 3306:3306 \
  --name mysql \
  --restart always \
  mysql:8.0 --default-authentication-plugin=mysql_native_password
```

### As client

```sh
docker run -it --rm mysql mysql -h 127.0.0.1 -P 3306 -u root -p
```

## Dump

```sh
docker run -it --rm -v $(pwd)/dump:/dump mysql sh -c 'mysqldump --column-statistics=0 -h 10.100.1.100 -P 3306 -u root -proot [database] > /dump/[filename].sql'
```
