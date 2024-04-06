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