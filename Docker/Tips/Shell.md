# Shell

## EOF

```sh
docker exec -i [container] sh << 'SHELL'
[script]
SHELL
```

###

```sh
docker exec -i [container] sh -c "$(cat << SHELL
[script]
SHELL
)"
```
