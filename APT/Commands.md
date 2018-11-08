# Commands

## Update

```sh
sudo apt update
```

## Install

```sh
sudo apt install -y [package]
```

## Upgrade

```sh
sudo apt upgrade -y
```

## Search

```sh
sudo apt search [package]
```

## Info

```sh
sudo apt-cache show [package]
```

## Show Dependencies

```sh
apt-cache rdepends [package]
```

## Remove

```sh
sudo apt-get remove [package]
```

### Purge

```sh
sudo apt-get remove --purge [package]
```

## Clean

```sh
sudo apt-get clean
```

### Remove

```sh
sudo rm -r /var/lib/apt/lists/*
```

## List

### Installed

```sh
sudo apt list --installed
```

### Upgradable

```sh
sudo apt list --upgradable
```
