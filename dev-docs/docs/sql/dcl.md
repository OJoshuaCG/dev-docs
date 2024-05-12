**DCL ("Data Control Language" o Lenguaje de Control de Datos)**

En estos tipos de comandos se otorgan los permisos que se le pueden permitir a los usuarios para controlar nuestro sistema de base de datos. Por ejemplo, seleccionar (`SELECT`), actualizar (`UPDATE`) o eliminar (`DELETE`), por mencionar algunos.


---

## GRANT

Permite otorgar permisos al usuario.

```sql
-- GRANT privilege ON db.table TO user@host

GRANT SELECT ON db.tbl_name TO 'username'@'localhost'; -- (1)

GRANT SELECT, INSERT, UPDATE, DELETE ON db.* TO 'username'@'localhost'; -- (2)

GRANT SELECT ON *.* TO 'username'@'localhost'; -- (3)

GRANT ALL PRIVILEGES ON db.tbl_name TO 'username'@'localhost'; -- (4)

GRANT SELECT ON db.tbl_name TO 'username'@'199.91.1.10'; -- (5)

GRANT SELECT ON db.tbl_name TO 'username'@'%'; -- (6)

GRANT SELECT ON db.tbl_name TO 'user1'@'host1', 'user2'@'host2'; -- (7)
```

1. Permitir utilizar el comando `SELECT` en una tabla en especifico con el usuario unicamente en `localhost`.
2. Permitir utilizar los comandos DML en todas las tablas de una base de datos.
3. Permitir utilizar el comando `SELECT` en cualquier base de datos y en cualquier tabla, unicamente en `localhost`.
4. Permitir utilizar todos los comandos.
5. Permitir utilizar el comando `SELECT` en una tabla en especifico con el usuario unicamente conectado en la IP `199.91.1.10`
6. Permitir utilizar el comando `SELECT` en una tabla en especifico con el usuario el cualquier `HOST` (`%`).
7. Permitir otorgar un privilegio a dos usuarios.


Para visualizar los permisos que se le ha otorgado al usuario, podemos seguir la siguiente serie de comandos

```sql
USE mysql;

SHOW GRANTS FOR 'user'@'host';
```


---

## REVOKE

Permite revocar los privilegios que se han otorgado con el comando `GRANT`.

Funciona muy similar al comando `GRANT`, la unica diferencia es que cambia la instruccion `TO` por `FROM`.

```sql
-- REVOKE privilege ON db.tbl FROM user@host
REVOKE SELECT ON db.tbl_name FROM user@host;

REVOKE UPDATE,DELETE,ALTER ON *.* FROM  'user'@'host';

REVOKE ALL PRIVILEGES ON *.* FROM 'user'@'host';
```


---

## Privilegios que se pueden otorgar

- ALL
- ALTER
- CREATE
- CREATE ROUTINE
- CREATE TEMPORARY TABLES
- CREATE USER
- CREATE VIEW
- DELETE
- DROP
- DROP ROLE
- EXECUTE
- FILE
- GRANT OPTION
- INDEX
- INSERT
- LOCK TABLES
- PROCESS
- PROXY
- REFERENCES
- RELOAD
- SELECT
- SHOW DATABASES
- SHOW VIEW
- SHUTDOWN
- SUPER
- TRIGGER
- UPDATE


---

## Fuentes

- [Mysql Dev Docs](https://dev.mysql.com/doc/refman/8.0/en/grant.html)
