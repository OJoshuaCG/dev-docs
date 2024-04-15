Al trabajar en un proyecto, es muy comun trabajar en equipo, tal vez cada persona tiene su flujo de trabajo propio, tal vez existan mas flujos de trabajo para **desarrollo**, **produccion**, **testing** u algun otro ambito que se desee.

Para todo esto, se suele apoyar de ramas o `branch`. Dentro de git podemos hacer uso de ellas.

## Branch

A continuacion, listaremos algunos de los comandos mas comunes

```sh
git branch # (1)
git branch <branch> # (2)

git branch -d <branch> # (3)
git branch -D <branch> # (4)

git branch -m <new-name> # (5)

git branch -a # (6)
```

1. Listar todas las ramas creadas
2. Crear una rama
3. Eliminar de manera segura una rama
4. Eliminar de manera forzada una rama
5. Cambiar nombre de la rama actual
6. Listar ramas remotas

Si deseamo eliminar una rama, debemos considerar que esta no cuente con `merges` pendientes, ya que de lo contrario, no podremos eliminar esta rama de forma habitual (`-d`) y deberemos forzar su eliminacion (`-D`)

Por otro lado, si contamos con varias ramas y deseamos que esten de manera remota, debemos hacerle un `push` a nuestra rama.

```sh
git push origin <branch>
```


---

### Cambiando de rama

Si deseamos cambiar de rama podemos apoyarnos del comando `checkout` el cual debemos pasar como parametro la rama a donde deseamos cambiar

```sh
git checkout <branch>
```

En caso que nuestra rama no exista, o deseamos cambiar a una rama nueva sin haberla creado previamente, nos podemos apoyar con la bandera `-b`

```sh
git checkout -b <branch>
```

!!! note "Nota"
    Hay que considerar que si tenemos cambios realizados sin haber hecho un commit (esten o no en la zona de `stage`) estaran moviendose conforme cambiemos de rama.

!!! warning "Atencion"
    Debido a la nota anterior, debemos considerar que si realizamos cambios a un archivo y la rama donde deseamos dirigirnos cuenta con cambios ya realizados sobre ese mismo archivo, podemos tener conflictos para cambiar a esa rama.

Si deseamos cambiar a una rama que se encuentra en un repositorio remoto, previamente, debemos obtener las ramas con ayuda del comando `fetch`

```sh
git fetch --all
```

Una vez obtenido las ramas, git nos indicara las ramas que hemos obtenido, por lo que ya podemos cambiar a esta nueva rama

```sh
git checkout <branch>
```

!!! info "Informacion"
    Con el comando `git fetch --all` logramos obtener todas las `branch` y `tag` que se encuentren de manera remota.