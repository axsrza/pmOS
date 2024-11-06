## Criar usuario e adicionar grupop

```bash

adduser user
addgroup user wheel

```

## Editar repositorio

```bash

vi /etc/apk/repositories

```

## Adiconar sudo e editar %wheel ALL=(ALL) ALL

```bash

apk update
apk add sudo
visudo

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
