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

## Jellyfin

```sh
./docker-compose-wrapper.sh jellyfin up -d
```

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

## Audiobookshelf

```sh
sudo -E bash mknasdir.sh    \
    audiobookshelf/config   \
    audiobookshelf/metadata

./docker-compose-wrapper.sh audiobookshelf up -d
```

## VPN

Add to your `.ovpn` file ip addresses if you want enable split tunneling

```
pull-filter ignore redirect-gateway

# route {ip} {mask}
route 1.2.3.4 255.255.255.255
route 5.6.7.8 255.255.255.255
```

```sh
./docker-compose-wrapper.sh vpn up -d
```
