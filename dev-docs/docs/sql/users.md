En esta seccion visualizaremos la gestion de los usuarios en MySQL.

La importancia de administrar usuarios es que nos permite tener controlado nuestro gestor de base de datos (MySQL).

Por ejemplo, si tenemos almacenadas varias bases de datos, podemos crear un usuario para cada una de ellas, ademas de solo darle los permisos necesarios sin comprometer la seguridad de nuestra base.

Antes de comenzar a utilizar los comandos, es importante que debes estar usando la base de `mysql`, ya que alli es donde se guarda toda la informacion de nuestros usuarios.

```sql
USE mysql;
```


---

## Creacion de usuario

Primeramente, debemos tener pensado en el nombre y su contraseña, ademas de conocer donde deseamos utilizar nuestro usuario:

- `localhost`. Ingreso del usuario unicamente dentro del servidor donde se encuentra la base de datos.
- `X.X.X.X`. Ingreso del usuario desde una IP en especifico
    - Es posible el uso de las mascaras, por ejemplo, `192.168.1.0/255.255.255.0`
- `%`. Ingreso del usuario desde cualquier lugar (IP)
    - Se puede utilizar el simbolo `%` en cualquier parte de la direccion IP para permitir el acceso, ejemplo, `192.168.1.%`, `45.200.%.%`.
    - Se puede utilizar el simbolo `%` en cualquier parte de un dominio para permitir el acceso, ejemplo, `%.mysql.com`


```sql
CREATE USER 'user'@'host' IDENTIFIED BY 'password';
```

!!! note "Nota"
    Despues de crear nuestro usuario o cualquier alteracion que hagamos en la tabla `user`, para que los cambios tengan efecto debemos recargar los privilegios:
    ```sql
    FLUSH PRIVILEGES;
    ```

Para visualizar nuestro usuario creado o los usuarios existentes debemos consultar la tabla `user`.

```sql
SELECT * FROM user;

SELECT user,host FROM user;
```

!!! note "Nota"
    Si deseamos permitir el ingreso de nuestro usuario desde 2 host diferentes, debemos agregarlo nuevamente cambiando el valor del host, se considerara como un nuevo usuario.


---

## Eliminar usuarios

Para eliminar un usuario y host en especifico, o solo por su usuario o por su host, podemos realizar lo siguiente.

```sql
DROP USER 'user'@'host'

DELETE FROM user WHERE user='user'

DELETE FROM user WHERE host='X.X.X.X'
```


---

## Modificar Usuario

Para cambiar la contraseña de un usuario debemos utilizar el comando `ALTER`

```sql
ALTER USER 'user'@'host' IDENTIFIED BY 'new_password';
```

!!! info "Informacion"
    Anteriormente, existia la columna `password` pero esta ha sido reemplaza por la columna `authentication_strin` en versiones mayores a MySQL 8.0, esta utilizando el plugin de seguridad `caching_sha2_password`

Si requerimos cambiar el host o el usuario, podemos utilizar el comando `UPDATE`

```sql
UPDATE user SET host='new_host' WHERE user='user' and host='host';
UPDATE user SET user='new_user' WHERE user='user' and host='host';
```