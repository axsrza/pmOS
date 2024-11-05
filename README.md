
## Verificar Serviços em Execução

```bash

rc-status

```

## Instalar o Docker

```bash

sudo apk add docker

```

## Iniciar o Docker

```bash

sudo service docker start

```

## Verificar a instalação do Docker

```bash

sudo docker run hello-world

```

## Instalar o Portainer

```bash

sudo docker run -d -p 9000:9000 --name portainer --restart always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data portainer/portainer-ce

```

## Verificar se o Docker está em execução

```bash

sudo service docker status

```

## Verificar contêineres em execução

```bash

sudo docker ps

```

## Criar usuario

```bash

adduser user
addgroup user wheel

```

## Editar Repositorio

```bash

vi /etc/apk/repositories

```

## Adiconar Sudo e editar %wheel ALL=(ALL) ALL

```bash

apk update
apk add sudo
visudo

```
