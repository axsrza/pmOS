## Instalar Docker:

```bash

sudo apk add docker

sudo service docker start

sudo rc-update add docker default

sudo docker info

sudo docker run --rm hello-world

```

## Whoogle:

```bash

sudo docker run --publish 5000:5000 --detach --name whoogle-search -v /var/lib/docker/volumes/whoogle-data:/whoogle-data benbusby/whoogle-search:latest

```

## Portainer:

```bash

sudo mkdir -p /var/lib/docker/volumes/portainer-data

sudo docker run --name portainer --publish 9000:9000 --publish 8000:8000 --volume /var/run/docker.sock:/var/run/docker.sock --volume /var/lib/docker/volumes/portainer-data:/data --detach portainer/portainer-ce:latest

```

## Obsidian:

```bash

sudo mkdir -p /var/lib/docker/volumes/obsidian-data

docker run -d --name=obsidian --security-opt seccomp=unconfined -e PUID=$(id -u) -e PGID=$(id -g) -e TZ=America/Sao_Paulo -p 3000:3000 -p 3001:3001 -v /var/lib/docker/volumes/obsidian-data:/config --device /dev/dri:/dev/dri --shm-size="1gb" --restart unless-stopped lscr.io/linuxserver/obsidian:latest

```
