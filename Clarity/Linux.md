# Linux

## Dependencies

### APT

```sh
sudo apt update
sudo apt install -y libmysqlclient-dev ruby-dev g++
```

Install gems

## Installation

```sh
sudo gem install mysql eventmachine eventmachine_httpserver json clarity
```

## Start server

```sh
sudo clarity --username=admin --password=admin --port=8989 /var/log
```

## Make Alias

```sh
alias clearlog='sudo rm /var/log/apache2/*; sudo systemctl restart apache2'
alias clearlog='sudo rm /var/log/nginx/*; sudo systemctl restart nginx'
```

## Restart Bash

```sh
source .bashrc
```

## Test Command

```sh
clearlog
```
