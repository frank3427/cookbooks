# Linux

## Installation

### YUM

```sh
sudo yum check-update
sudo yum -y install ntp
```

```sh
ntpdate 0.rhel.pool.ntp.org
```

## Service

```sh
sudo systemctl enable --now ntpd
```
