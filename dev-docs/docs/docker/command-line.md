Dentro de la terminal existen distintos comandos que se acompañan de distintas banderas para cumplir un proposito especifico, se estaran listando aquellos comandos mas comunes con sus banderas ademas del escenario para ser ejecutados

## Comandos basicos

```sh
docker ps # Lista los contenedores en ejecucion
docker ps -a # Lista todos los contenedores existentes en el sistema

```

## `pull`

Con este comando podemos descargar una imagen. Estas imagenes se encuentran el [Docker Hub](https://hub.docker.com/), existen diversas, ademas de alli mismo indicarnos como obtener las imagenes y especificar alguna version deseada.

```sh
docker pull nginx # Por defecto se descargara la version 'latest'
docker pull nginx:latest

docker pull nginx:bookworm
docker pull nginx:alpine
docker pull nginx:alpine3.21
docker pull nginx:1.27.4-alpine
docker pull nginx:1.27.4-alpine3.21
```


---

## `run`

Permite ejecutar y crear un contenedor a traves de una imagen, esta imagen sera descargada en caso de no encontrarse en el sistema.
Suele acompañarse este comando junto con algunas banderas.

| Bandera | Funcion |
| :--- | --- |
| `-d, --detach` | Ejecutar imagen en segundo plano (background) |
| `--name`  | Asigna un nombre al contenedor que desea crearse |
| `-p, --publish` | Mapeo de puertos (`puerto-host:puerto-contenedor`, `8080:80`) |
| `-v, --volume` | Montaje de volumen (`directorio-host:directorio-contenedor`, `./src:/var/www/`) |
| `--rm` | Elimina automaticamente el contenedor cuando es detenido |
| `-i, --interactive` | Mantiene la entrada del teclado activa |
| `-t, --tty` | Asigna o abre una terminal dentro del contenedor |
| `-it` | Combinacion de las 2 banderas anteriores, permite interactuar con el contenedor a traves de la terminal |
| `--workdir` | Carpeta a utilizar. |
| `-e, --env` | Establece variables de entorno |
| `-m` | Limite de memoria a utilizar |


_Algunas banderas pueden contener parametros, mientras que otras no (`-d`, `--rm`, `-it`)._

```sh
# Ejecutar MySQL con variables de entorno
docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mypassword mysql:latest

# Ejecutar un servidor web Nginx mapeando puertos y en segundo plano
docker run -d -p 80:80 -v /path/on/host:/var/www/html --name mi-sitio-web nginx:latest

# Ejecutar MySQL con variables de entorno y volumen persistente
docker run -d --name mi-db -e MYSQL_ROOT_PASSWORD=mi-clave-secreta -e MYSQL_DATABASE=app_db -v mysql_data:/var/lib/mysql -p 3306:3306 mysql:8.0

# Ejecutar una aplicación Node.js con volúmenes para desarrollo
docker run -it --rm -v $(pwd):/app -w /app -p 3000:3000 node:14 npm start

# Ejecutar una aplicación en modo interactivo con entrypoint personalizado
docker run -it --rm --entrypoint /bin/bash python:3.9

# Ejecutar Wordpress conectado a MySQL existente
docker run -d --name mi-wordpress -p 8080:80 --link mi-db:mysql -e WORDPRESS_DB_HOST=mysql -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=mi-clave-secreta -e WORDPRESS_DB_NAME=app_db wordpress

# Ejecutar PostgreSQL con variables de entorno y red personalizada
docker run -d --name mi-postgres --network=app-network -e POSTGRES_PASSWORD=secreto -e POSTGRES_USER=admin -e POSTGRES_DB=miapp -p 5432:5432 postgres:13

# Ejecutar una aplicación con variables de entorno desde un archivo
docker run -d --name mi-app --env-file ./variables.env -p 5000:5000 mi-aplicacion:1.0

# Ejecutar phpMyAdmin conectado a un contenedor MySQL existente
docker run -d --name phpmyadmin -p 8081:80 --link mi-db:db -e PMA_HOST=db phpmyadmin/phpmyadmin
```


## `exec`

Nos permite interactuar con el contenedor ejecutando comandos dentro de el, gracias a este comando poder ingresar a la terminal de nuestro contenedor.

Se cuentan con algunas banderas disponibles del comando `docker run`, como por ejemplo:

| Bandera | Funcion |
| :--- | --- |
| `-d, --detach` | Ejecutar el comando en segundo plano (background) |
| `-i, --interactive` | Mantiene la entrada del teclado activa |
| `-t, --tty` | Asigna o abre una terminal dentro del contenedor |
| `-it` | Combinacion de las 2 banderas anteriores, permite interactuar con el contenedor a traves de la terminal |
| `-u, --user` | Ejecuta el comando con un usuario en especifico. |
| `-w, --workdir` | Ubicacion donde se ejecutara el comando. |
| `-e, --env` | Establece variables de entorno |
| `--privileged` | Otorga al comando privilegios elevados. |
| `--cpu-shares` Asigna acciones de CPU al comando. |

```sh
# Visualizaremos el directorio actual
docker exec mi_contenedor ls -l

# Acceso directo a la terminal activa del contenedor
docker exec -it mi_contenedor /bin/bash

# Ejecutar un comando como un usuario específico
docker exec -u www-data mi_contenedor php artisan migrate

# Ejecutar un comando en un directorio de trabajo específico
docker exec -w /var/www mi_contenedor ls -l

# Ejecutar un comando con variables de entorno:
docker exec -e DEBUG=true mi_contenedor python my_script.py

# Ejecutar un comando en un contenedor en segundo plano (detached)
docker exec -d mi_contenedor /app/mi_script_largo.sh

# Ejecutar un comando con privilegios elevados
docker exec --privileged mi_contenedor iptables -L

# Asignar más recursos a un comando
docker exec --cpu-shares 512 mi_contenedor ./mi_programa_intensivo
```
