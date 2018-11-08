# Linux

## Installation

### YUM

```sh
sudo yum check-update
sudo yum -y install openssh-server
```

### APT

```sh
sudo apt update
sudo apt install -y openssh-server
```

## Service

```sh
sudo systemctl enable --now sshd
```
