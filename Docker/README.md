# Docker

## Presenter: Jefferson Ferreira
### Date: 05/25/2022

Docker presentation with Jefferson on 05/25/2022.

[Click here](https://youtu.be/YL-yxooEixU) to watch video class about Docker.

## Dockerfile

The Dockerfile is a text file with instructions, commands and steps that you would manually perform, the Docker cake recipe.

[Click here](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/) to about how creating Dockerfiles using the best practices and methods for building efficient images.
```
ADD => Copia novos arquivos, diretórios, arquivos TAR ou arquivos remotos e os adicionam ao filesystem do container;
ex.: ADD . /src

CMD => Executa um comando, diferente do RUN que executa o comando no momento em que está "buildando" a imagem, o CMD executa no início da execução do container;
ex.: CMD ["-D", "FOREGROUND"]

LABEL => Adiciona metadados a imagem como versão, descrição e fabricante;
ex.: LABEL description="Webserver"

COPY => Copia novos arquivos e diretórios e os adicionam ao filesystem do container;
ex.: COPY --from=buildando /src/goapp /app

ENTRYPOINT => Permite você configurar um container para rodar um executável, e quando esse executável for finalizado, o container também será;
ex.: ENTRYPOINT ["/usr/sbin/apachectl"]

ENV => Informa variáveis de ambiente ao container;
ex.: ENV APACHE_LOG_DIR="/var/log/apache2"

EXPOSE => Informa qual porta o container estará ouvindo;
ex.: EXPOSE 80

FROM => Indica qual imagem será utilizada como base, ela precisa ser a primeira linha do Dockerfile;
ex.: FROM golang AS buildando

MAINTAINER => Autor da imagem; 
ex.: 

RUN => Executa qualquer comando em uma nova camada no topo da imagem e "commita" as alterações. Essas alterações você poderá utilizar nas próximas instruções de seu Dockerfile;
ex.: RUN apt-get update && apt-get install -y apache2 && apt-get clean

USER => Determina qual o usuário será utilizado na imagem. Por default é o root;
ex.: USER www-data

VOLUME => Permite a criação de um ponto de montagem no container;
ex.: VOLUME /var/www/html/

WORKDIR => Responsável por mudar do diretório / (raíz) para o especificado nele;
ex.: WORKDIR /src
```
# Docker Compose v2
Docker Compose is a tool that was developed to help define and share multi-container applications. With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.

[Click here](https://docs.docker.com/get-started/08_using_compose/#:~:text=Docker%20Compose%20is%20a%20tool,or%20tear%20it%20all%20down.) to about how creating and use a docker-compose.yml.

[![Actions Status](https://github.com/docker/compose/workflows/Continuous%20integration/badge.svg)](https://github.com/docker/compose/actions)

Docker Compose is a tool for running multi-container applications on Docker
defined using the [Compose file format](https://compose-spec.io).
A Compose file is used to define how the one or more containers that make up
your application are configured.
Once you have a Compose file, you can create and start your application with a
single command: `docker compose up`.

# About update and backward compatibility

Docker Compose V2 is a major version bump release of Docker Compose. It has been completely rewritten from scratch in Golang (V1 was in Python). The installation instructions for Compose V2 differ from V1. V2 is not a standalone binary anymore, and installation scripts will have to be adjusted. Some commands are different.

For a smooth transition from legacy docker-compose 1.xx, please consider installing [compose-switch](https://github.com/docker/compose-switch) to translate `docker-compose ...` commands into Compose V2's `docker compose .... `. Also check V2's `--compatibility` flag.

# Where to get Docker Compose

### Windows and macOS

Docker Compose is included in
[Docker Desktop](https://www.docker.com/products/docker-desktop)
for Windows and macOS.

### Linux

You can download Docker Compose binaries from the
[release page](https://github.com/docker/compose/releases) on this repository.

Rename the relevant binary for your OS to `docker-compose` and copy it to `$HOME/.docker/cli-plugins` 

Or copy it into one of these folders for installing it system-wide:

* `/usr/local/lib/docker/cli-plugins` OR `/usr/local/libexec/docker/cli-plugins`
* `/usr/lib/docker/cli-plugins` OR `/usr/libexec/docker/cli-plugins`

(might require to make the downloaded file executable with `chmod +x`)


Quick Start
-----------

Using Docker Compose is basically a three-step process:
1. Define your app's environment with a `Dockerfile` so it can be
   reproduced anywhere.
2. Define the services that make up your app in `docker-compose.yml` so
   they can be run together in an isolated environment.
3. Lastly, run `docker compose up` and Compose will start and run your entire
   app.

A Compose file looks like this:

```yaml
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
  redis:
    image: redis
```

Contributing
------------

Want to help develop Docker Compose? Check out our
[contributing documentation](CONTRIBUTING.md).

If you find an issue, please report it on the
[issue tracker](https://github.com/docker/compose/issues/new/choose).

# Alguns Comandos...

## Relacionados às informações

- docker info ou docker system info - Lista a quantidade de contêineres e imagens e informações do ambiente.

- docker system df - Exibe a quantidade de imagens, contêineres, se estão ativos ou não, espaço ocupado em disco.

- docker version - Exibe a versão do docker que está instalada.

- docker inspect ID_CONTAINER - Retorna diversas informações sobre o container.

- docker ps ou docker container ls - Exibe todos os containers em execução no momento.

- docker ps -a ou docker container ls -a - Exibe todos os containers, independentemente de estarem em execução ou não.

- docker diff container_name_ou_id - Inspeciona as alterações que foram feitas no interior do contêiner.


## Relacionados à Monitoramento

- docker stats - Exibe a estatística de uso dos containeres.
- docker container stats container_id – Exibe a quantidade de uso de memoria e CPU que o contêiner esta consumindo.


## Relacionados à execução

- CRTL + P + Q – Sai de um container mas permanece em execução.

- docker container attach container_id – Entra no container em execução

- docker run NOME_DA_IMAGEM - Cria um container com a respectiva imagem passada como parâmetro.

- docker run -it NOME_DA_IMAGEM - Conecta o terminal que estamos utilizando com o do container.

- docker run -d -P --name NOME dockersamples/static-site - Ao executar, dá um nome ao container e define uma porta aleatória.

- docker run -d -m 128M id_container - Cria um container com 128 mb. Limitando/Configurando o uso de memoria RAM do container. (Pode usar o parâmetro --memory ao invés de -m)

- docker run -d --cpus 0.5 --memory 50M id_container - Cria um container com 50% de 1 core de CPU e 50mb de RAM. Limitando/Configurando o uso de CPU  do container

- docker container update --cpus 0.2  id_container - Altera/Atualiza as informações de uso de CPU do container

- docker run -d -p 12345:80 dockersamples/static-site - Define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.

- docker commit -m “mensage” id_container ou image_name:tag - Cria uma imagem tageada a partir de um container com comentário

- docker image tag image_id new_name:tag - Nomeia ou Renomeia uma imagem

- docker image prune (cuidado!!!) - Limpa todas as imagens, desde que não estejam sendo usadas por nenhum contêiner.

- docker system prune (cuidado!!!) - Limpa todas as imagens, contêineres, redes não utilizadas por nenhum contêiner.

- docker port ID_DO_CONTAINER - Permite saber qual porta da máquina faz referência à porta "xxxx" de seu container.


## Relacionados à inicialização/interrupção

- docker start ID_CONTAINER - Inicia o container

- docker restart ID_CONTAINER - Reinicia o container

- docker start -a -i ID_CONTAINER - Inicia o container e integra os terminais além de permitir interação entre ambos.

- docker stop ID_CONTAINER - Interrompe o container

- docker pause ID_CONTAINER - Pausa o container

- docker unpause ID_CONTAINER - Despausa o container

- docker container logs -f ID_CONTAINER - Mostra os logs do container


## Relacionados à remoção

- docker rm ID_CONTAINER - Remove o container com id em questão.

- docker rm -f ID_CONTAINER - Remove o container com id em questão.

- docker container prune - Remove todos os containers que estão parados.

- docker rmi NOME_DA_IMAGEM - Remove a imagem passada como parâmetro.

- docker rmi -f NOME_DA_IMAGEM - Remove a imagem em execução passada como parâmetro.

## Relacionados à Volumes

#### Volume do tipo BIND:

- docker run -v "[CAMINHO_HOST:CAMINHO_CONTAINER]" --name CONTAINER_NAME IMAGE_NAME - Cria um volume no respectivo caminho do container, caso seja especificado um caminho local monta o volume local no volume do container.


#### Volume do tipo VOLUME:

- docker container run -it --mount type=volume,src=/host_dir/host_dir/host_dir,dst=/container_dir/ container_dir image_name/container_id  - Monta um diretório do host em um diretório dentro do contêiner.


## Relacionados ao docker-compose

- docker-compose build - Realiza o build dos serviços relacionados ao arquivo docker-compose.yml, assim como verifica a sua sintaxe.

- docker-compose up - Sobe todos os containers relacionados ao docker-compose, desde que o build já tenha sido executado.

- docker-compose down - Para todos os serviços em execução que estejam relacionados ao arquivo docker-compose.yml.

- docker-compose ps - lista os serviços que estão rodando.

- docker exec -it CONTAINER_NAME ping node2 - executa o comando ping node2 dentro do container CONTAINER_NAME

- docker-compose exec “service-name-on-docker-compose” ls -l – Lista o diretório raíz do container


## Relacionados à Rede

- docker network create --driver bridge NOME_DA_REDE - Cria uma rede especificando o driver desejado.

- docker inspect NOME_DA_REDE - Inspeciona os dados da rede.

- docker network connect NOME_DA_REDE  NOME_DO_CONTAINER - Conecta um container a uma rede docker criada.

- docker network disconnect NOME_DA_REDE  NOME_DO_CONTAINER – Desconecta um container a uma rede docker criada.

- docker network create --driver bridge NOME_DA_REDE - Cria uma rede especificando o driver desejado.

- docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM - Cria um container especificando seu nome e qual rede deverá ser usada.


## Registry Público (Docker Hub)

- docker login - Login no Docker Hub.
 
- docker push NOME_USUARIO/NOME_IMAGEM - Envia a imagem criada para o Docker Hub.
 
- docker pull NOME_USUARIO/NOME_IMAGEM - Baixa a imagem desejada do Docker Hub.


## Registry Privado com senha

- docker login registry.suaempresa.com - Loga no registry local.

- docker container run -d -p 5000:5000 –restart=always –name “registry_name” registry:2  - Cria um repositório docker local (local registry).

- docker push "endereco_registry:PORTA/image_name:tag - Empurra a imagem para um repositório (docker registry 
local).

- curl -X GET https://myregistry:5000/v2/_catalog - Lista todos os repositórios (efetivamente imagens).


## Registry sem senha:

- curl -X GET https://myregistry:5000/v2/REPO_OR_IMAGE_NAME/tags/list - Lista todas as tags para um repositório.

#### Se o registro estiver protegido por senha, use:

- curl -u <user>:<pass> -X GET https://myregistry:5000/v2/_catalog

- docker exec -it id_container_registry sh - Entra no contêiner do registry

  
## Diretório das imagens dentro do contêiner do registry:

- var/lib/registry/docker/registry/v2/repositories/image_name

  
## Relacionados ao docker-compose
  
- docker-compose build - Realiza o build dos serviços relacionados ao arquivo docker-compose.yml, assim como verifica a sua sintaxe.
  
- docker-compose up - Sobe todos os containers relacionados ao docker-compose, desde que o build já tenha sido executado.
  
- docker-compose down - Para todos os serviços em execução que estejam relacionados ao arquivo docker-compose.yml.
  
- docker-compose ps - lista os serviços que estão rodando.
  
- docker exec -it aula-books-1 ping node2 - Executa o comando ping node2 dentro do container aula-books-1
  
- docker-compose exec “service-name-on-docker-compose” ls -l - Lista o diretório raíz do container.
    
  
# Utilitários:  
  
- Docker Desktop [Click here](https://docs.docker.com/get-docker/)
  
- ctop - Utilitário Linux que exibe a estatística de uso dos containeres
  ```
  sudo apt install ctop
  ```

- Portainer [Click here](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)

