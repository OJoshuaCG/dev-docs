El `commit` nos ayuda a pasar todos los cambios de la zona `stage` a la zona de `snapshot`.
De esta forma podremos tener un control de todos los cambios que realicemos.

Es importante tener en cuenta que previamente, debemos tener archivos en nuestra zona de `stage`, de lo contrario, no sera posible realizar un `commit`


---

## Realizando un commit.

Es muy sencillo, ademas de poder agregar un mensaje a nuestro `snapshot` que nos ayuda a brindar detalles de la version.

```sh
git commit -m "Descripcion del snapshot"
```

Para agregar el mensaje con ayuda de nuestro editor de texto configurado con git, podemos realizarlo de la siguiente manera

```sh
git commit
git commit -a
```

Si nuestro proyecto a cambiado, tenemos archivos que podemos agregar a la zona de `stage`, pero no los hemos agregado (`add`), podemos utilizar el siguiente comando, el cual agregara todos los cambios realizados a la zona de `stage` mientras que al mismo tiempo realizara un `commit`

```sh
git commit -am "Descripcion del snapshot"
```


---

## Modificar un commit

Podemos modificar el mensaje del ultimo commit realizado (**unicamente es posible con el ultimo commit**), podemos hacer uso de la bandera `--amend`

```sh
git commit --amend -m "Mensaje a modificar"
```

En el escenario donde necesitemos agregar o modificar los archivos, y agregarlos al ultimo commit (modificarlo), podemos realizar lo siguiente:

```sh
# Agregar primeramente los archivos
git add file1 file2
git add .
# Modificar ultimo commit
git commit --amend -m "Ultimo commit modificado"

# O si deseamos agregar todos los archivos y hacerlo con un solo comando
git commit --amend -am "Ultimo commit modificado"
```


---

## Revertir commit

Dentro de git, podemos revertir o eliminar nuestro commit. Lo cual existen 2 maneras:

- Mantener los cambios. Con la flag `--soft` nos permitira regresar a un commit manteniendo los cambios realizados en el estado actual.

```sh
git reset --soft HEAD~1 # (1)
```

1. Regresaremos un commit atras, podemos pasar **N** commit atras cambiando el valor de **1**.

- No mantener cambios. Con el flag `--hard` nos permite regresar a un commit eliminando los cambios realizados en nuestros archivos y regresandolos al estado en que se encontraban en ese commit

```sh
git reset --hard HEAD~1
```

Tambien es posible regresar a un commit en especifico pasandole su id hash

```sh
git log --oneline
git reset --soft abcd123
```


<!-- ---

## Regresar a un commit en especifico

git log -10 --pretty="%H"
git reset --hard 484121a5ed21e8b842ffe61783fde059103185b3
git checkout ab25f1ln2b4o3a9c4u1v6k4n1m7 .

git rebase -i HEAD~1

git reset [--mixed] HEAD~1


eliminar commits remotos
git revert 74a1092
 -->
