Cuando trabajamos con Git en un proyecto, desearemos guardar nuestros cambios del proyecto para despues realizar el famoso `commit`, sin embargo, antes de ejecutar este comando debemos agregar (`add`) archivos que deseamos hacer commit, estos archivos se encontraran en la zona de `stage`, ademas, si contamos con archivos los cuales no deseamos agregar al commit, podemos reservarlos con el comando `stash`, los cuales no se tomaran en cuenta al realizar nuestro commit.


## Estado del proyecto

Con este comando conoceremos el status de nuestro proyecto, es funcional para conocer que archivos sufrieron algun cambio, si tenemos pendiente hacer un commit o realizar un `push` a nuestro repositorio

```sh
git status

# Result:
- Changes not staged for commit:
    deleted: file1
    modified: file2
    new file: file3

- Untracked files:
    file4.txt

- Changes to be commited:

- nothing to commit, working tree clean
```


---

## Agregar archivos

Este comando es muy simple, nos permitira agregar uno o mas achivos a la zona de `stage` para despues realizar un `commit`. Para ello podemos especificar el (los) archivo(s) o unicamente agregar todos con ayuda del punto (`.`)

```sh
git add file1 file2 ./path/file3

# Agregar todos los archivos con cambios
git add .
```


---

## Remover archivos

Dentro de git, cuando estamos agregando archivos, los colocamos en la zona `stage`, despues de este paso podremos hacer un `commit`, sin embargo, si deseamos remover uno o mas archivos de la zona de `stage`, podemos hacer uso del comando `restore` con ayuda de una bandera

```sh
git restore --staged file.txt
```

Si deseamos revertir los cambios de un archivo (remover todos los cambios que le hemos realizado), podemos utilizar el mismo comando sin ayuda de alguna bandera

```sh
git restore file.txt
```

<!-- Alternativas
git rm --cached
git reset -->


---

## Limpiando  archivos

Hemos visto como agregar archivos y como eliminarlos de nuestra zona de `stage`, sin embargo, git tambien nos ofrece la capacidad de eliminar los archivos que no se encuentran en el **historial de git**.

Por ejemplo, al crear un archivo o directorio nuevo que no hemos agregado previamente al historial (`git add`), git nos permite limpiar nuestro proyecto con ayuda del comando `git clean`, sin embargo, necesita de forzarse con ayuda de la bandera `-f`

```sh
git clean -f
```

Ademas de ello, podemos visualizar previamente los archivos que se van a limpiar con ayuda de la bandera `-n`

```sh
git clean -n
```

Sin embargo, esto lo realiza a nivel de archivos, para que pueda considerar los directorios (carpetas), debemos pasar la bandera `-d`

```sh
git clean -dn

git clean -df
```

Al aplicar el comando `git clean -f` no considera los archivos ignorados de nuestro `.gitignore`, sin embargo, si deseamos eliminar estos archivos, podemos apoyarnos de la bandera `-x`

```sh
git clean -xn

git clean -xf
```

!!! note "Nota"
    Esta ultima bandera `-x` tambien considera los archivos, pero no los directorios, sin embargo podemos hacer una combinacion de las banderas, como por ejemplo

    ```sh
    git clean -xdn

    git clean -xdf
    ```


!!! danger "Aviso"
    Tenga cuidado al aplicar un `git clean` ya que puede eliminar archivos que deseamos conservar en nuestro proyecto.