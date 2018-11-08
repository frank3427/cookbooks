# Auth

## Ubuntu

```sh
sudo tee -a /etc/squid3/squid.conf << EOF
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwords
auth_param basic realm proxy
acl authenticated proxy_auth REQUIRED
http_access allow authenticated
EOF
```

```sh
sudo apt install -y apache2-utils
```

```sh
sudo htpasswd -c /etc/squid3/passwords [username]
```

```sh
sudo systemctl restart squid3
```
