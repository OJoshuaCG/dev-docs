Para poder instalar docker (en windows), requerimos instalar WSL, para ello tendremos que elegir una distribucion de linux la cual instalaremos en nuestro sistema.

Podemos ver las opciones con el siguiente comando:

```sh
wsl --list --online
```

Una vez que tengamos en mente que distribucion elegir, vamos a instalarla con el siguiente comando

```sh
wsl --install -d <distro>

wsl --install -d Debian
```

Una vez instalada nuestra distribucion, podemos llevar a cabo la instalacion de [Docker Desktop](https://www.docker.com/products/docker-desktop/).