## Mariadb

Vamos a llevar a cabo la creacion de una base de datos de [MariaDB con Docker](https://hub.docker.com/_/mariadb), para ello, elegiremos una imagen en especifico o utilizar la ultima version `latest`, en nuestro caso elegimos la version `11.6.2`

```sh
docker pull mariadb:11.6.2
```

Una vez descargada la imagen, vamos a crear nuestro contenedor, por ejemplo, si deseamos que tenga una contraseña en especifico, nos  apoyamos de la bandera `--env` y el parametro `MARIADB_ROOT_PASSWORD`

```sh
docker run --detach --name dbmaria -p 3306:3306 --env MARIADB_ROOT_PASSWORD=password mariadb:11.6.2
```

Despues de crear el contenedor, consideraremos los siguientes parametros de conexion:

- User: `root`
- Password: `my-secret-pw`
- Host: `localhost`
- Port: `3306`


---

## SQL Server

Procederemos a obtener la imagen de [SQL Server con docker](https://hub.docker.com/r/microsoft/mssql-server), podemos elegir entre sus versiones de 2017, 2019, 2022.

```sh
docker pull mcr.microsoft.com/mssql/server
docker pull mcr.microsoft.com/mssql/server:2022-latest
docker pull mcr.microsoft.com/mssql/server:2019-latest
docker pull mcr.microsoft.com/mssql/server:2017-latest
```

Para poder ejecutar la imagen, se requieren de al menos 2 banderas, la tercera siendo opcional:

- "ACCEPT_EULA=Y"
- "MSSQL_SA_PASSWORD=<your_strong_password>"
- "MSSQL_PID=<your_product_id | edition_name> (default: Developer)"

```sh
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=password" -p 1433:1433 -d --name dbmssql mcr.microsoft.com/mssql/server:2019-latest
```


---

## Postgresql

En el caso de [Postgresql con docker](https://hub.docker.com/_/postgres/tags?page=3) es mas sencillo, debemos buscar la imagen de la version que deseamos obtener, y descargamos la imagen.

```sh
docker pull postgres:16-bookworm
```

Para poder crear nuestro contenedor, requerimos unicamente de la variable `POSTGRES_PASSWORD` para asignar la contraseña

```sh
docker run --name dbpostgres -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres:16-bookworm
```


---

## MongoDB

Vamos a utilizar una imagen para una base de datos NoSQL, en nuestro caso [MongoDB](https://hub.docker.com/r/mongodb/mongodb-community-server)

```sh
docker pull mongodb/mongodb-community-server:7.0.15-ubuntu2204
```

Al crear nuestro contenedor, podemos establecer un usuario y contraseña para nuestra bse de datos

```sh
docker run --name dbmongo -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=user -e MONGO_INITDB_ROOT_PASSWORD=password mongodb/mongodb-community-server:7.0.15-ubuntu2204
```