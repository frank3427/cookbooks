# VisitorGenerator

## Installation

```sh
git clone https://github.com/matomo-org/plugin-VisitorGenerator.git plugins/VisitorGenerator
```

## Active

```sh
./console plugin:activate VisitorGenerator
```

## Generate

### Anonymize log

```sh
./console visitorgenerator:anonymize-log [file]
```

### Annotation

```sh
./console visitorgenerator:generate-annotation --idsite 1
```

### Goals

```sh
./console visitorgenerator:generate-goals --idsite 1
```

### Users

```sh
./console visitorgenerator:generate-users --limit 100
```

### Visits

```sh
./console visitorgenerator:generate-visits --idsite 1 --days 2
```

#### Live

```sh
./console visitorgenerator:generate-live-visits --idsite 1
```

#### Websites

```sh
./console visitorgenerator:generate-websites --limit 10
```

#### Shorten log

```sh
./console visitorgenerator:shorten-log [file]
```
