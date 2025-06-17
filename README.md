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
```
Para acceder al contenedor y poder conectarlo a s1
```bash
docker exec -it c1 bash
```


