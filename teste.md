
## Descomentar linha http://dl-cdn.alpinelinux.org/alpine/v3.20/community


```bash

vi /etc/apk/repositories

```

Para salvar aperte ESC :wq

## Adicionar sudo e editar %wsudo ALL=(ALL) ALL

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

## Desligar computador:

```bash

sudo poweroff

```


## Ao iniciar o sistema, conecte o usb ao computador e execute no console DO CELULAR:

```bash

ip a

```

Algo assim deve ser exibido:

usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 96:0d:c8:fc:23:2f brd ff:ff:ff:ff:ff:ff
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

eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether fa:48:e7:bb:81:7c brd ff:ff:ff:ff:ff:ff
    inet 172.16.42.2/16 scope global eth1

## Connect via SSH:

```bash

ssh user@172.16.42.1

```

## Adicionar rede wifi:

```bash

wpa_passphrase "rozza_5G" "Esquina@238" | sudo tee /etc/wpa_supplicant/wpa_supplicant.conf 

```

## Verificar arquivo da rede:

```bash

nano /etc/wpa_supplicant/wpa_supplicant.conf

network={
        ssid="rozza_5G"
        #psk="Esquina@238"
        psk=676ed05ab65b5456f1ab780a758459b24401865040c736ef798fff1988710bae
}

```

## Adicionar network:

```bash

nano /etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

## Adicionar network default:

```bash

sudo rc-update add networking default

```

## Ativar e pegar ip:

```bash

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D nl80211 -B
sudo udhcpc -i wlan0

```

## Adicionar wpa default:

```bash

sudo rc-update add wpa_supplicant default

```
