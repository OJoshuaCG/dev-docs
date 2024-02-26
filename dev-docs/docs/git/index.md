## Git

Git es un software para el control de versiones.
Nos permite tener un avance de nuestro proyecto para darle un mantenimiento. Es multiplataforma y utilizado en los repositorios para poder administrar nuestro codigo en la nube de manera remota.

Su instalacion es muy sencilla, puedes realizar este proceso a traves del siguiente [enlace](https://git-scm.com/download/)


---

## Primeros pasos

Para poder iniciar tu proyecto con Git, basta con ejecutar el comando `init` con `git` dentro de la carpeta donde se encontrara nuestro proyecto, todo esto a nivel de consola o linea de comandos.

```sh
git init
```

Para poder agregar archivos, se hace uso del comando `add`, el cual, nos permitira agregar los archivos de forma individual o todos a la vez.
La unica condicion, es que estos archivos deben de ser nuevos, o previamente debieron ser modificados (actualizados o eliminados).

```sh
# Agregar un archivo en especifico
git add path/folder/file.ext
git add file.ext

# Agregar todos los archivos nuevos/modificados
git add .
```

Por ultimo debemos guardar estos cambios con ayuda del comando `commit`, el cual suele ir acompañado de una breve descripcion del cambio realizado con ayuda de la bandera `-m`, por ejemplo: _Inicio del proyecto_, _Modulo de pago agregado_, _Vista de cliente eliminada_, _Modificacion del dashboard_, ....

```sh
git commit -m "Mensaje. Descripcion de los cambios"

# Ejemplo
git commit -m "Modulo de pago agregado"
```

Estos son los primeros pasos para sobrevivir con Git, sin embargo, este software contiene muchas mas funcionalidades, los cuales estaremos describiendo los mas comunes a lo largo de la documentacion.
