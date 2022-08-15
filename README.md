# Proxy-inverso

Esta documentación tiene como evidenciar el código y configuración que se utilizó para crear un reverse proxy con Nginx.

## Ejecución de la aplicación en docker-compose

En la máquina virtual que contiene Docker, se ejecutará una aplicación de la siguiente forma:

- Ejecutar el siguiente comando en una terminal
```
export CLOUDSDK_PYTHON=/usr/bin/python2
```
- Crear un archivo 'script.sh'
```
nano script.sh
```
- Copiar las siguientes lineas
```
#!/usr/bin/env bash
CURRENT_WORKDIR=$(pwd)
FILE_ID="1EH1zS1wQ_5WmvUEar2eXcB4QMj1Mo49g"
FILENAME="docker-compose-example.tgz"
mkdir example && cd example
wget --no-check-certificate "https://docs.google.com/uc?export=download&id=${FILE_ID}" -O ${FILENAME}
tar xfz ${FILENAME}
cd ${CURRENT_WORKDIR}
```
- Cambiar los permisos de ejecución del script y ejecutarlo
```
chmod +x script.sh && ./script.sh
```
- Ingresar al directorio **example** y ejecutar ***docker-compose***
```
cd example && docker-compose up
```
- Entrar a un navegador y escribir en el buscador **localhost:8000** o **192.168.28.31:8000**

## Creación servidor web apache

En otra máquina virtual se instalará apache para correr un servidor web en el puerto 80. Para ello se realizará lo siguiente:

- Ejecutar el siguiente comando en una terminal
```
sudo apt update
```
- Instalar apache
```
sudo apt install apache
```
- Abrir un navegador y escribir **localhost** o **192.168.28.32**
- Se puede modificar el archivo **index.html** en la ruta ***/var/www/html*** para mostrar algo distinto al estilo por defecto.
