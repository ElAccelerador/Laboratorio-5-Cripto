# Laboratorio 5 - Análisis de Tráfico SSH con Docker y Wireshark

Este repositorio contiene los Dockerfiles utilizados en el laboratorio para generar tráfico SSH entre diferentes versiones de OpenSSH, así como los comandos necesarios para levantar los contenedores y replicar los experimentos.

##  Requisitos

- Docker instalado
- Wireshark (opcional, para análisis de tráfico)

##  Paso 1: Crear la red compartida

```bash
docker network create ssh-net
```
## Paso 2: Construcción de imágenes

```bash
# C1
docker build -t c1-img -f C1 .

# C2
docker build -t c2-img -f C2 .

# C3
docker build -t c3-img -f C3 .

# C4 (servidor)
docker build -t c4-img -f C4 .

```
##  Paso 3: Levantar los contenedores

```bash
docker run -dit --name s1 --hostname s1 --network ssh-net -p 2222:22 c4-img

docker run -dit --name c1 --network ssh-net c1-img

docker run -dit --name c2 --network ssh-net c2-img

docker run -dit --name c3 --network ssh-net c3-img

```
Para acceder al contenedor C1 y poder conectarlo a s1
```bash
docker exec -it c1 bash
```
Para acceder al contenedor C2 y poder conectarlo a s1
```bash
docker exec -it c2 bash
```
Para acceder al contenedor C3 y poder conectarlo a s1
```bash
docker exec -it c3 bash
```
Para acceder al contenedor C4 y poder conectarlo a s1
```bash
docker exec -it s1 bash
```
Para hacer la conexion al servidor con C1, C2, C3
```bash
ssh prueba@s1
```
Para hacer la conexion al servidor con C4, el anterior comando puede servir, pero se recomienda
```bash
ssh prueba@localhost
```
Las conexiones al servidor tienen que ser individuales, y ya al momento de realizar la conexion se pedirá una contraseña, la cual será "prueba".



