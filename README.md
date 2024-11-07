Apos a instalação logar como root

## Descomentar linha #http://dl-cdn.alpinelinux.org/alpine/v3.20/community

```bash

vi /etc/apk/repositories

```

Para salvar aperte ESC :wq

## Adicionar sudo e editar descomentar #%sudo ALL=(ALL) ALL

```bash

apk update
apk add sudo
visudo

```

Para salvar aperte ESC :wq

## Criar usuario e adicionar grupo

```bash

adduser user

addgroup sudo

adduser user sudo

```

## Instalar pmbootstrap:

```bash

apk add pmbootstrap

```

## Entrar como user:

```bash

su - user

```

## Iniciar pmbootstrap:

```bash

pmbootstrap init

pmbootstrap pull

```

## Criar recovery zip image:

```bash

pmbootstrap install --android-recovery-zip

```

## Sideload:

Boot the recovery system

Unmount the partitions (Click on "Mount", then deselect all checkboxes)

Click on "Advanced / ADB Sideload", then "Swipe to start sideload"

Connect your phone to your PC

Start the sideloading process from your PC:

```bash

pmbootstrap flasher --method=adb sideload

```

Apos a instalação voltar como root: su -

## Ao iniciar o sistema, conecte o usb ao computador e execute no console DO CELULAR:

```bash

ip a

```

Algo assim deve ser exibido:

usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 0000 qdisc pfifo_fast state UP qlen 0000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 172.16.42.1/16 brd 172.16.255.255 scope global usb0

## Execute no console DO COMPUTADOR:

```bash

dmesg | grep usb

```

No meu caso ele esta eth1

## Setar ip eht1:

```bash

ip addr add 172.16.42.2/16 dev eth1
ip link set eth1 up

```

## Verificar se deu certo:

```bash

ip a

```

Algo assim deve ser exibido:

eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 0000 qdisc pfifo_fast state UP qlen 0000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 172.16.42.2/16 scope global eth1

## Connect via SSH:

WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
Execute: ssh-keygen -R 172.16.42.1

```bash

ssh user@172.16.42.1

```

## Listar e adicionar rede wifi:

```bash

sudo nmcli device wifi list ifname wlan0

sudo nmcli device wifi connect "$SSID" password "$PASSWORD" ifname "wlan0"

```

## Alterar senha root:

```bash

sudo passwd root

```

## Testar alteração:

```bash

su

passwd

```

## Descomentar linhas #Port 22 #PermitRootLogin yes(alterar para yes) #PasswordAuthentication yes #PermitEmptyPasswords no

```bash

sudo nano /etc/ssh/sshd_config

```

Executar poweroff no host e reboot o celular

## Verificar se deu certo NO CELULAR:

```bash

ip a

```

## Podman:

```bash

sudo apk add podman

podman info

podman run --rm hello-world

```

## Desativar firewall:

```bash

sudo nft flush ruleset

```

## Podman Whoogle-search:

```bash

sudo podman pull benbusby/whoogle-search

sudo podman run --publish 5000:5000 --detach --name whoogle-search benbusby/whoogle-search:latest

```

## Docker:

```bash

sudo apk add docker

sudo service docker start

sudo rc-update add docker default

sudo docker info

sudo docker run --rm hello-world

```

## Docker Whoogle-search:

```bash

sudo docker pull benbusby/whoogle-search

sudo docker run --publish 5000:5000 --detach --name whoogle-search benbusby/whoogle-search:latest

```
