# GIT PRACTICA 1

## Conceptos básicos de Git
* Git se basa en snapshots (instantáneas) del código en un estado determinado, que viene dado por el autor y la fecha
* Un Commit es un conjunto de cambios guardados en el repositorio de Git y tiene un identificador SHA1 único
* Las ramas (branches) se pueden pensar como una línea de tiempo a partir de los commit. Hay siempre como mínimo una rama principal o predefinida llamada Master
* Head es el puntero al último commit en la rama activa
* Remote se refiere a sitios que hospedan repositorios remotos como GitHub, BitBucket o GitLab

## Conectarse a una sesión de GitPod
1) Crear un nuevo repositorio en nuestro GitHub llamado "my_git" e inicializarlo con el archivo README de forma automática
* Se puede hacer un fork de https://github.com/Juli-BCN/my_git
2) Abrir una sesión en GitPod con el nuevo respositorio, que seria una URL parecida a esta:
```
https://gitpod.io#https://github.com/Juli-BCN/my_git
```

## Ayuda de Git
Con `git help` en el terminal obtenemos ayuda. Vamos a mirar la ayuda de configuración con:
> git help config


## Configuración de Git
Como mínimo debemos configurar el nombre y el email en la aplicación con el comando `git config`:
> git config --global user.name "Nombre Apellido"

> git config --global user.email "tu_email_aqui@ejemplo.com"

Para comprobar podemos usar:
> git config -–global –list


## Trabajar en un proyecto existente con Git
Aunque existe un comando específico para crear un nuevo repositorio (`git init`), lo más normal será conectarse a un repositorio existente en nuestro SCM, como GitLab o GitHub. Para ello, deberemos clonar el repositorio existente con el comando `git clone`. Aunque en este caso, como el repositorio existe en GitHub y lo hemos abierto en GitPod, este paso podemos omitirlo.

Podemos ver que al conectarnos GitPod o a un repositorio clonado, se crea automaticamente un directorio oculto llamado `.git` que contiene toda la informacion de los objetos de Git, como branches, HEAD, logs, objects, refs, etc.:
> ls -la

> ls -la .git


## Primer commit
Ahora vamos a crear algún archivo en el primero de los proyectos. Podemos crear uno llamado `INFO.txt` y pondremos el contenido "Archivo para Git":
> nano INFO.txt

Podemos mirar si hay cambios pendientes con el comando `git status`:
> git status

Aquí podemos ver que estamos en la rama principal llamada "main" y que tenemos un archivo llamado `INFO.txt` que aún no se ha agregado al repositorio. Para agregar un archivo a un commit usaremos el comando `git add`, que se puede usar de dos maneras
1) > git add nombre_de_archivo --> agrega solo el archivo especificado
2) > git add . --> agrega todos los archivos nuevos

Asi estamos preparados para hacer el commit a nuestro repositorio con el comando `git commit` que tiene el parametro `-m` para poner un mensaje al commit:
> git commit -m "commit inicial"
