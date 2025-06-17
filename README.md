# Laboratorio 5 - Análisis de Tráfico SSH con Docker y Wireshark

Este repositorio contiene los Dockerfiles utilizados en el laboratorio para generar tráfico SSH entre diferentes versiones de OpenSSH, así como los comandos necesarios para levantar los contenedores y replicar los experimentos.

##  Requisitos

- Docker instalado
- Wireshark (opcional, para análisis de tráfico)

---

##  Paso 1: Crear la red compartida

```bash
docker network create ssh-net

