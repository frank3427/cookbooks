# Docker

## Volume

```sh
docker volume create matomo-data
docker volume create matomo-logs
docker volume create nginx-conf
```

## Running

```sh
docker run -d \
  -h matomo \
  -v matomo-data:/var/www/html \
  -v matomo-logs:/var/www/html/logs \
  -p 9000:9000 \
  --name matomo \
  --restart always \
  matomo:3.9.1-fpm-alpine
```

```sh
docker run -d \
  -h nginx \
  -v nginx-conf:/etc/nginx/conf.d \
  -v matomo-data:/var/www/html \
  -p 8080:80 \
  --name nginx \
  --restart always \
  nginx:1.15.8-alpine
```

```sh
docker exec -i nginx sh << 'SHELL'
cat << 'EOF' > /etc/nginx/conf.d/default.conf
upstream matomo {
    server matomo:9000;
}

server {
    listen 80 default_server;
    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        fastcgi_pass matomo;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location = /health-check {
        access_log off;
        default_type application/json;
        return 200 '{"status": "UP"}';
    }
}
EOF
SHELL
```

```sh
docker restart nginx
```

```sh
echo -e "[INFO]\thttp://$(hostname -I | awk '{print $1}'):8080"
```

##

```sh
docker run -it \
  -v matomo-data:/var/www/html \
  alpine/git:1.0.7 clone https://github.com/matomo-org/plugin-VisitorGenerator.git /var/www/html/plugins/VisitorGenerator
```

```sh
docker exec -it matomo /usr/local/bin/php /var/www/html/console plugin:activate VisitorGenerator
```

```sh
docker exec -it matomo /usr/local/bin/php /var/www/html/console visitorgenerator:generate-visits \
  --idsite 1 \
  --days 1 \
  -vvv
```

## Archive

```sh
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_browser_archiving_triggering' --value='0'
```

```sh
docker exec -it matomo /bin/su -s '/bin/sh' -c '/usr/local/bin/php /var/www/html/console core:archive' www-data
```

## Misc

```sh
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_trusted_host_check' --value='0'
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_sql_optimize_queries' --value='0'
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_marketplace' --value='0'
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_internet_features' --value='0'
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_auto_update' --value='0'
docker exec -it matomo /usr/local/bin/php /var/www/html/console config:set --section='General' --key='enable_update_communication' --value='0'
```
