## DDL ("Data Definition Language" o Lenguaje de Definicion de Datos)

Estos son comandos que pueden ser utilizados para definir el esquema de nuestra base de datos, como la creacion (`CREATE`), eliminar (`DROP`), modificar (`ALTER`) y truncar (`TRUNCATE`).

Solo es utilizado para modificar la estructura pero no la informacion de ella. Suelen ser comandos los cuales no otorgamos privilegios a usuarios generales, ya que al modificar la estructura de la base de datos o tabla, pueden provocar confusiones en el desarrollo.


## `CREATE`

Este comando es utilizado para crear una base de datos o sus objetos como table (`table`), indices (`index`), vistas (`views`), procedimientos almacenados (`store procedures`) y `triggers`

Algunos ejemplos:

```sql
CREATE DATABASE database_name;

CREATE TABLE tbl_name(
  column1 datatype (size),
  column2 datatype (size),
  -- ...
  columnN datatype (size),
);

CREATE INDEX index_name ON tbl_name(
  column1, column2, ...
);
```


---

## `DROP`

Con el comando `DROP` nos permitira eliminar bases de datos o sus objetos

Algunos ejemplos:

```sql
DROP TABLE tbl_name;

DROP DATABASE databse;
```


---

## `ALTER`

Es usualmente utilizado para realizar modificaciones en la estructura de nuestra base de datos, muy comunmente en nuestras tablas.

Se suelen complementar con otros comandos como `ADD`, `DROP`, `MODIFY`, `RENAME`, entre otros.

Algunos ejemplos:

```sql
ALTER TABLE tbl_name ADD COLUMN column1 datatype (size);

ALTER TABLE tbl_name DROP COLUMN column1;

ALTER TABLE tbl_name MODIFY column_name new_datatype (new_size);

ALTER TABLE tbl_name RENAME TO new_tbl_name;
ALTER TABLE tbl_name RENAME COLUMN column1 TO new_column_;
```


---

## `TRUNCATE`

EL comando `TRUNCATE` nos permite eliminar todas las filas dentro de una tabla, conservando la estructura de nuestra tabla.

```sql
TRUNCATE TABLE tbl_name;
```