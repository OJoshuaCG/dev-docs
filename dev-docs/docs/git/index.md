## Git

Git es un software para el control de versiones.
Nos permite tener un avance de nuestro proyecto para darle un mantenimiento. Es multiplataforma y utilizado en los repositorios para poder administrar nuestro codigo en la nube de manera remota.

Su instalacion es muy sencilla, puedes realizar este proceso a traves del siguiente [enlace](https://git-scm.com/download/)

Durante esta documentacion, estaremos viendo los comandos mas comunes, asi como aquellos que utilizamos en caso de X o Y situacion, por ejemplo, revertir un commit, cambiar de rama sin perder los cambios realizados, fusionar ramas, buenas practicas para los commits, entre otros.

---


## Configuracion

Antes de iniciar con Git, debemos realizar una pequeña configuracion, donde debemos agregar un nombre y correo como referencia para futuros commit.
Para ello, nos ayudaremos del comando `config` y su bandera `--global`

```sh
git config --global user.name "Usuario"
git config --global user.email "correo@mail.com
```

Una vez configurado esta parte, podemos visualizar la informacion con ayuda del siguiente comando:

```sh
git config --global -l
```

---


## Iniciar en un proyecto

Para poder iniciar tu proyecto con Git, basta con ejecutar el comando `init` con `git` dentro de la carpeta donde se encontrara nuestro proyecto, todo esto a nivel de consola o linea de comandos.

```sh
git init
```

Para poder agregar archivos, utilizamos el comando `add`, el cual, nos permitira agregar los archivos de forma individual o todos al mismo tiempo.
La unica condicion, es que estos archivos deben de ser nuevos, o previamente, debieron ser modificados (actualizados o eliminados).

```sh
# Agregar un archivo en especifico
git add path/folder/file.ext
git add file.ext

# Agregar todos los archivos nuevos/modificados
git add .
```

Por ultimo debemos guardar estos cambios con ayuda del comando `commit`, el cual suele ir acompañado de una breve descripcion del cambio realizado con ayuda de la bandera `-m`, por ejemplo: "_Inicio del proyecto_", "_Modulo de pago agregado_", "_Vista de cliente eliminada_", "_Modificacion del dashboard_", ....

```sh
git commit -m "Mensaje. Descripcion de los cambios"

# Ejemplo
git commit -m "Modulo de pago agregado"
```

Estos son los primeros pasos para sobrevivir con Git, sin embargo, este software contiene muchas mas funcionalidades, las cuales estaremos describiendo a lo largo de esta documentacion.
