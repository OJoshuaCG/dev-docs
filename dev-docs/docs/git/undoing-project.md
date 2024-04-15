En algunas ocasiones, cuando trabajamos con git, tendemos a equivocarnos al realizar un commit, tal vez un archivo no deseabamos que estuviera en ese commit, el commit no tiene relevancia, nos hemos equivocado en su contenido o algo mas.

En esta seccion visualizaremos como eliminar un commit (`reset`) y como revertir un commit `revert`.


---

## Resetear commit

Dentro de git, podemos resetear o eliminar nuestro commit, con ayuda del commando `reset`.

Esto nos permite regresar a un `commit` en especifico, sin embargo, el historial de cambios de git se vera afectado, de modo, que todos los cambios realizados despues de este `commit` ya no se mostraran en el historial de git.

Se puede aplicar de dos maneras:

- _**Mantener los cambios**_. Con la flag `--soft` nos permitira regresar a un commit manteniendo los cambios realizados en el estado actual (o de los demas estados).

```sh
git reset --soft HEAD~1 # (1)
```

1. Regresaremos un commit atras, podemos pasar **N** commit atras cambiando el valor de **1**.

---

- _**No mantener cambios**_. Con el flag `--hard` nos permite regresar a un commit eliminando los cambios realizados en nuestros archivos y regresandolos al estado en que se encontraban en ese commit

```sh
git reset --hard HEAD~1
```

!!! tip
    Si realizamos un `git reset` sin flags, automaticamente realizara el `reset` de manera '`soft`'

---

Tambien es posible regresar a un commit en especifico pasandole su id hash

```sh
git log --oneline
git reset --soft abcd123
```


!!! note "Nota"
    Si deseamos resetear o eliminar estos commits de nuestro repositorio remoto podemos seguir los siguientes pasos:

    ```sh
    git reset abcd123 # (1)
    git push -f origin main # (2)
    ```

    1. Reseteamos a un commit en especifico
    2. Hacemos un `push` de manera forzada con la bandera `-f`


---

## Revertir commit

Previamente vimos como "resetar un commit", el cual nos permite "eliminar commits" o realizar un reseteo a un commit en especifico, reiniciando el historial de cambios de git de nuestro proyecto-rama, de modo que perdemos todos los commits realizados, con la opcion de mantener los cambios hechos en nuestros archivos.

Sin embargo, podemos realizar estos "reseteos" sin perder el historial de cambios de git, esto con ayuda del commando `revert`

```sh
git revert HEAD # (1)
git revert abcd123 # (2)
```

1. Revertir el ultimo commit
2. Revertir a un commit en especifico

---

!!! warning "Aviso"
    `git revert` nos permitira regresar a un estado de un `commit`, lo cual, perdemos los cambios hechos, sin embargo, el historial de cambios de `git`, se mantendra intacto.



---

## Conclusion

`git reset` nos permite mover nuestro puntero de cambios (`HEAD`) a un `commit` en especifico, olvidando el historial de cambios de git que hubo despues de ese `commit`.

`git revert` nos permite regresar el proyecto al estado en el que se encontraba el `commit` el cual deseamos regresar, creando un nuevo "`commit`", permitiendo mantener el historial de cambios de git.
