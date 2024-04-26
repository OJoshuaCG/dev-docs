DML ("Data Manipulation Language" o Lenguaje de Manipulacion de Datos)

Estos comandos nos permiten interactuar con la informacion de nuestras tablas. Gracias a ellas podremos consultar, insertar, actualizar o eliminar la informacion.


## `SELECT`

El comando `SELECT` es utilizado para consultar los registros de nuestra tabla.

```sql
SELECT * FROM tbl_name;

SELECT column1, column2, ... FROM tbl_name;
```


---

## `INSERT`

Este comando nos permitira llenar de informacion nuestra base de datos.

```sql
INSERT INTO tbl_name VALUES (value1, value2, value3);

INSERT INTO tbl_name (column1, column2, column3) VALUES (value1, value2, value3);

INSERT INTO tbl_name (column1, column2, column3) VALUES
  (value1, value2, value3),
  (value1, value2, value3),
  (value1, value2, value3),
  ...;
```


---

## `UPDATE`

La sentencia `UPDATE` es utilizado para actualizar la informacion existente en las tablas. Puede realizarse sobre una sola columna o sobre varias.

Suele estar acompañada del comando `WHERE`, el cual permitira realizar la actualizacion de datos de acuerdo a una condicion establecida.

```sql
UPDATE tbl_name SET column1 = value1, column2 = value2, ...; -- (1)

UPDATE tbl_name SET column1 = value1, column2 = value2, ...
WHERE condition;
```

1. Actualizara todas las filas

---

## `DELETE`

El comando `DELETE`, es una operacion utilizada para eliminar la informacion en nuestras tablas.

A diferencia del comando `DROP`, `DELETE` preserva la tabla, unicamente realiza la eliminacion de las fila(s) de las tabla

Al igual que el comando `UPDATE`, es comun ser utilizado con el comando `WHERE`.

```sql
DELETE FROM tbl_name; -- (1)

DELETE * FROM tbl_name; -- (2)

DELETE FROM tbl_name WHERE condition
```

1. Eliminara todas las filas
2. Eliminara todas las filas
