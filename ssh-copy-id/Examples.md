# Examples

## Generate

```sh
ssh-keygen -t rsa -b 4096 -C '[email]'
```

## Copy id

```sh
ssh-copy-id -i ~/.ssh/id_rsa [username]@[hostname]
```

## Test

```sh
ssh -i ~/.ssh/id_rsa [username]@[hostname]
```
