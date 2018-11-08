# Clone

```sh
mysql -ve 'CREATE DATABASE IF NOT EXISTS [db-name]' -u [username] -p
```

```sh
mysqldump -u [username] --password=[password] [db-name] | mysql -u [username] --password=[password] [db-name]
```
