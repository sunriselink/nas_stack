# My NAS stack

## First steps

- Create a `nas` user
- Add current user to `nas` group
- Fill missing variables in `global.env`

Or for debugging execute

```sh
source .debugrc
```

## Portainer

```sh
./docker-compose-wrapper.sh portainer up -d
```

`http://localhost:9000`

## Jellyfin

```sh
./docker-compose-wrapper.sh jellyfin up -d
```

`http://localhost:8096`

## Nextcloud

```sh
sudo -E bash mknasdir.sh    \
    nextcloud/config        \
    nextcloud/custom_apps   \
    nextcloud/data          \
    nextcloud/postgres_data \
    nextcloud/themes

./docker-compose-wrapper.sh nextcloud up -d
```

`http://localhost:8080`

## Audiobookshelf

```sh
sudo -E bash mknasdir.sh    \
    audiobookshelf/config   \
    audiobookshelf/metadata

./docker-compose-wrapper.sh audiobookshelf up -d
```

`http://localhost:13378`

## Monitoring (TIG - Telegraf + InfluxDB + Grafana)

```sh
sudo -E bash mknasdir.sh        \
    monitoring/grafana/data     \
    monitoring/influxdb         \
    monitoring/influxdb/config  \
    monitoring/influxdb/data

./docker-compose-wrapper.sh monitoring up -d
```

`http://localhost:3000`

Default `login:password` is `admin:admin`
