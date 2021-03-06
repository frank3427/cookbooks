# Configuration

## Main

```sh
sudo tee /etc/krb5.conf << EOF
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 dns_lookup_realm = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 rdns = false
 default_ccache_name = KEYRING:persistent:%{uid}

EOF
```

## Keytabs

```sh
sudo mkdir -p /etc/security/keytabs
```

## Realm

```sh
sudo sed -i '/\[libdefaults\]/a \ default_realm = [DOMAIN.COM]' /etc/krb5.conf
```

```sh
sudo tee -a /etc/krb5.conf << EOF
[realms]
 [DOMAIN.COM] = {
  kdc = [kdc.domain.com]
  admin_server = [kdc.domain.com]
 }

[domain_realm]
 [.domain.com] = [DOMAIN.COM]
 [domain.com] = [DOMAIN.COM]

EOF
```
