# Examples

## Cells

```sh
vtctlclient -server localhost:15999 GetCellInfoNames
```

```sh
vtctlclient -server localhost:15999 GetCellInfo [cell]
```

## Generic

```sh
vtctlclient -server localhost:15999 ListAllTablets [cell]
```

## Apply Schema

### SQL

```sh
vtctlclient -server localhost:15999 ApplySchema -sql "$(cat [filename].sql)" [database]
```

### Virtual Schema

```sh
vtctlclient -server localhost:15999 ApplyVSchema -vschema "$(cat [filename].json)" [database]
```

## Running

```sh
vtctlclient -server localhost:15999 MigrateServedTypes vitess/0 master
```

## Jobs

| Name | Kind | Cell | Command |
| --- | --- | --- | --- |
| `mst0` | `vtctlclient` | `zone1` | `MigrateServedTypes [shard]/0 [master|rdonly|replica]` |
| `dsr0` | `vtctlclient` | `zone1` | `DeleteShard -recursive [shard]/0` |
| `cks` | `vtctlclient` | `zone1` | `CreateKeyspace -served_from='master:[shard],replica:[shard],rdonly:[shard]' [shard]` |
| `msf0` | `vtctlclient` | `zone1` | `MigrateServedFrom [shard]/0 [master|rdonly|replica]` |
| `sstc0` | `vtctlclient` | `zone1` | `SetShardTabletControl -blacklisted_tables=[shard1],corder -remove [shard2]/0 [master|rdonly|replica]` |
| `vsc0` | `vtworker` | `zone1` | `VerticalSplitClone -min_healthy_rdonly_tablets=1 -tables=[shard],corder [shard]/0` |
| `scm0` | `vtworker` | `zone1` | `SplitClone -min_healthy_rdonly_tablets=1 [shard]/0` |

### Example

```yml
jobs:
  - name: mst0
    kind: vtctlclient
    cell: zone1
    command: 'MigrateServedTypes customer/0 master'
```
