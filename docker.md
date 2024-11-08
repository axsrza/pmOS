## Instalar Docker:

```bash

sudo apk add docker

sudo service docker start

sudo rc-update add docker default

sudo docker info

sudo docker run --rm hello-world

```

## Whoogle no sdcard:

```bash

sudo mkdir -p /mnt/sdcard

sudo mount /dev/mmcblk0p1 /mnt/sdcard

sudo mkdir /mnt/sdcard/whoogle-data

sudo podman run --publish 5000:5000 --detach --name whoogle-search -v /mnt/sdcard/whoogle-data:/whoogle-data benbusby/whoogle-search:latest

```

## Portainer no sdcard:

```bash

sudo mkdir -p /mnt/sdcard/portainer-data

sudo docker run --name portainer --publish 9000:9000 --publish 8000:8000 --volume /var/run/docker.sock:/var/run/docker.sock --volume /mnt/sdcard/portainer-data:/data --detach portainer/portainer-ce:latest

```
