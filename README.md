# Docker
# 12345678.MD

## Índice de Comandos Docker

### Docker Engine
1. [docker system prune](#docker-system-prune)
2. [docker info](#docker-info)
3. [docker ps](#docker-ps)
4. [docker images](#docker-images)
5. [docker run](#docker-run)
6. [docker stop](#docker-stop)
7. [docker start](#docker-start)
8. [docker rm](#docker-rm)
9. [docker rmi](#docker-rmi)
10. [docker build](#docker-build)
11. [docker pull](#docker-pull)
12. [docker push](#docker-push)
13. [docker exec](#docker-exec)
14. [docker logs](#docker-logs)
15. [docker network](#docker-network)
16. [docker volume](#docker-volume)

### Docker Compose
1. [docker compose up](#docker-compose-up)
2. [docker compose down](#docker-compose-down)
3. [docker compose build](#docker-compose-build)
4. [docker compose logs](#docker-compose-logs)
5. [docker compose ps](#docker-compose-ps)
6. [docker compose restart](#docker-compose-restart)

### Docker Swarm
1. [docker swarm init](#docker-swarm-init)
2. [docker swarm join](#docker-swarm-join)
3. [docker swarm leave](#docker-swarm-leave)
4. [docker node ls](#docker-node-ls)
5. [docker service ls](#docker-service-ls)
6. [docker service create](#docker-service-create)
7. [docker service scale](#docker-service-scale)
8. [docker stack deploy](#docker-stack-deploy)
9. [docker stack ls](#docker-stack-ls)
10. [docker stack rm](#docker-stack-rm)

---

## Docker Engine

### docker system prune
**Descripción:** Elimina todos los recursos no utilizados (contenedores, imágenes, redes, volúmenes) para liberar espacio en disco.

**Opciones disponibles:**
- `--all` o `-a`: Elimina todas las imágenes no utilizadas
- `--force` o `-f`: Ejecuta sin confirmación
- `--volumes`: Elimina volúmenes no utilizados
- `--filter`: Filtra qué eliminar usando condiciones

**Ejemplo:**
```bash
docker system prune --all --volumes --force
docker info
Descripción: Muestra información detallada del sistema Docker instalado.

Opciones disponibles:

--format: Formatea la salida con plantilla Go

-f: Formato específico de salida

Ejemplo:

bash
docker info
docker info --format '{{.ServerVersion}}'
docker ps
Descripción: Lista contenedores en ejecución.

Opciones disponibles:

-a: Muestra todos los contenedores (incluyendo detenidos)

-q: Muestra solo IDs de contenedores

--filter: Filtra contenedores por condiciones

--format: Formatea la salida

Ejemplo:

bash
docker ps -a
docker ps --filter "status=running"
docker images
Descripción: Lista imágenes Docker disponibles localmente.

Opciones disponibles:

-a: Muestra todas las imágenes (incluyendo intermedias)

-q: Muestra solo IDs de imágenes

--filter: Filtra imágenes por condiciones

--no-trunc: Muestra IDs completos

Ejemplo:

bash
docker images
docker images --filter "dangling=true"
docker run
Descripción: Crea y ejecuta un nuevo contenedor a partir de una imagen.

Opciones disponibles:

-d: Ejecuta en segundo plano (detached)

-it: Modo interactivo con terminal

--name: Asigna nombre al contenedor

-p: Mapea puertos (host:container)

-v: Monta volúmenes

--network: Conecta a una red específica

-e: Define variables de entorno

Ejemplo:

bash
docker run -d --name mi-contenedor -p 8080:80 nginx
docker run -it ubuntu:20.04 /bin/bash
docker stop
Descripción: Detiene uno o más contenedores en ejecución.

Opciones disponibles:

-t: Tiempo de espera antes de forzar parada (default 10s)

Ejemplo:

bash
docker stop mi-contenedor
docker stop $(docker ps -q)
docker start
Descripción: Inicia uno o más contenedores detenidos.

Opciones disponibles:

-a: Adjunta STDOUT/STDERR y reenvía señales

-i: Adjunta la entrada estándar del contenedor

Ejemplo:

bash
docker start mi-contenedor
docker start contenedor1 contenedor2
docker rm
Descripción: Elimina uno o más contenedores.

Opciones disponibles:

-f: Fuerza eliminación (contenedores en ejecución)

-v: Elimina volúmenes asociados

-l: Elimina enlaces específicos

Ejemplo:

bash
docker rm mi-contenedor
docker rm -f $(docker ps -aq)
docker rmi
Descripción: Elimina una o más imágenes.

Opciones disponibles:

-f: Fuerza eliminación

--no-prune: No elimina etiquetas no referenciadas

Ejemplo:

bash
docker rmi mi-imagen:latest
docker rmi $(docker images -q)
docker build
Descripción: Construye una imagen desde un Dockerfile.

Opciones disponibles:

-t: Etiqueta para la imagen

--file: Especifica Dockerfile a usar

--build-arg: Define variables de construcción

--no-cache: Construye sin usar cache

Ejemplo:

bash
docker build -t mi-app:1.0 .
docker build -t mi-app --build-arg VERSION=1.0 .
docker pull
Descripción: Descarga una imagen desde un registro.

Opciones disponibles:

-a: Descarga todas las etiquetas de la imagen

--platform: Especifica plataforma objetivo

Ejemplo:

bash
docker pull nginx:latest
docker pull ubuntu:20.04
docker push
Descripción: Sube una imagen a un registro.

Opciones disponibles:

No tiene opciones principales adicionales

Ejemplo:

bash
docker push mi-usuario/mi-imagen:1.0
docker exec
Descripción: Ejecuta un comando en un contenedor en ejecución.

Opciones disponibles:

-it: Modo interactivo con terminal

-d: Ejecuta en segundo plano

-u: Usuario específico para ejecutar

-w: Directorio de trabajo

Ejemplo:

bash
docker exec -it mi-contenedor /bin/bash
docker exec mi-contenedor ls -la
docker logs
Descripción: Muestra logs de un contenedor.

Opciones disponibles:

-f: Sigue mostrando logs en tiempo real

--tail: Número de líneas a mostrar desde el final

-t: Muestra timestamps

--since: Muestra logs desde timestamp específico

Ejemplo:

bash
docker logs mi-contenedor
docker logs -f --tail=50 mi-contenedor
docker network
Descripción: Gestiona redes Docker.

Comandos principales:

docker network ls: Lista redes

docker network create: Crea nueva red

docker network inspect: Inspecciona red

docker network connect: Conecta contenedor a red

docker network disconnect: Desconecta contenedor de red

Ejemplo:

bash
docker network ls
docker network create mi-red
docker network connect mi-red mi-contenedor
docker volume
Descripción: Gestiona volúmenes Docker.

Comandos principales:

docker volume ls: Lista volúmenes

docker volume create: Crea nuevo volumen

docker volume inspect: Inspecciona volumen

docker volume rm: Elimina volumen

docker volume prune: Elimina volúmenes no utilizados

Ejemplo:

bash
docker volume ls
docker volume create mi-volumen
docker volume prune
Docker Compose
docker compose up
Descripción: Crea e inicia servicios definidos en docker-compose.yml.

Opciones disponibles:

-d: Ejecuta en segundo plano

--build: Reconstruye imágenes antes de iniciar

--force-recreate: Recrea contenedores incluso sin cambios

--scale: Escala servicios específicos

Ejemplo:

bash
docker compose up -d
docker compose up --build --scale web=3
docker compose down
Descripción: Detiene y elimina contenedores, redes, volúmenes e imágenes creados por up.

Opciones disponibles:

-v: Elimina volúmenes declarados en la sección volumes

--rmi: Elimina imágenes usadas por los servicios

--remove-orphans: Elimina contenedores huérfanos

Ejemplo:

bash
docker compose down
docker compose down -v --remove-orphans
docker compose build
Descripción: Construye o reconstruye servicios.

Opciones disponibles:

--no-cache: Construye imágenes sin usar cache

--pull: Siempre intenta obtener versión más reciente de la imagen

Ejemplo:

bash
docker compose build
docker compose build --no-cache --pull
docker compose logs
Descripción: Muestra logs de los servicios.

Opciones disponibles:

-f: Sigue mostrando logs

--tail: Número de líneas a mostrar

-t: Muestra timestamps

servicio: Filtra por servicio específico

Ejemplo:

bash
docker compose logs
docker compose logs -f --tail=100 web
docker compose ps
Descripción: Lista contenedores de los servicios.

Opciones disponibles:

-a: Muestra todos los contenedores

--services: Muestra servicios

--filter: Filtra por condiciones

Ejemplo:

bash
docker compose ps
docker compose ps --services
docker compose restart
Descripción: Reinicia servicios.

Opciones disponibles:

-t: Tiempo de espera para reinicio

Ejemplo:

bash
docker compose restart
docker compose restart web database
Docker Swarm
docker swarm init
Descripción: Inicializa un swarm y hace al nodo actual manager.

Opciones disponibles:

--advertise-addr: Dirección para que otros nodos se conecten

--listen-addr: Dirección para escuchar conexiones

--data-path-addr: Dirección para datos del swarm

Ejemplo:

bash
docker swarm init --advertise-addr 192.168.1.100
sudo docker swarm init --advertise-addr $(hostname -I | awk '{print $1}')
docker swarm join
Descripción: Une un nodo al swarm como worker o manager.

Opciones disponibles:

--token: Token para unirse al swarm

--advertise-addr: Dirección para anunciar el nodo

--listen-addr: Dirección para escuchar

Ejemplo:

bash
docker swarm join --token SWMTKN-1-example 192.168.1.100:2377
docker swarm leave
Descripción: Hace que el nodo abandone el swarm.

Opciones disponibles:

--force: Fuerza abandono incluso si es manager

Ejemplo:

bash
docker swarm leave
docker swarm leave --force
docker node ls
Descripción: Lista nodos en el swarm.

Opciones disponibles:

-q: Muestra solo IDs de nodos

--filter: Filtra nodos por condiciones

Ejemplo:

bash
docker node ls
docker node ls --filter role=manager
docker service ls
Descripción: Lista servicios en el swarm.

Opciones disponibles:

-q: Muestra solo IDs de servicios

--filter: Filtra servicios por condiciones

Ejemplo:

bash
docker service ls
docker service ls --filter name=web
docker service create
Descripción: Crea un nuevo servicio.

Opciones disponibles:

--replicas: Número de réplicas del servicio

--publish: Publica puertos

--mount: Monta volúmenes o bind mounts

--network: Conecta a una red

--env: Define variables de entorno

--constraint: Define restricciones de colocación

Ejemplo:

bash
docker service create --name web --replicas 3 -p 80:80 nginx
docker service scale
Descripción: Escala el número de réplicas de un servicio.

Opciones disponibles:

servicio=num: Especifica servicio y número de réplicas

Ejemplo:

bash
docker service scale web=5
docker service scale web=3 api=2
docker stack deploy
Descripción: Despliega una nueva stack o actualiza una existente.

Opciones disponibles:

-c o --compose-file: Archivo compose a usar

--with-registry-auth: Envía credenciales de registro

--prune: Elimina servicios que ya no están en el compose

Ejemplo:

bash
docker stack deploy -c docker-compose.yml mi-stack
sudo docker stack deploy -c swarm.yml billing
docker stack ls
Descripción: Lista stacks en el swarm.

Opciones disponibles:

No tiene opciones principales adicionales

Ejemplo:

bash
docker stack ls
docker stack rm
Descripción: Elimina una stack del swarm.

Opciones disponibles:

No tiene opciones principales adicionales

Ejemplo:

bash
docker stack rm mi-stack
