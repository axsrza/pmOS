
## descomentar linha http://dl-cdn.alpinelinux.org/alpine/v3.20/community


```bash

vi /etc/apk/repositories

```

para salvar aperte ESC :wq

## Adiconar sudo e editar %wsudo ALL=(ALL) ALL

```bash

apk update
apk add sudo
visudo

```

para salvar aperte ESC :wq

## Criar usuario e adicionar grupop

```bash

adduser user
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
