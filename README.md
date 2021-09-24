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

## Permitir a GitPod publicar cambios en nuestro GitHub
1) Ir a https://gitpod.io/access-control/ o https://gitpod.io/integrations
2) Pulsar en los tres botones a la derecha de GitHub > Edit Permissions
3) Marcar "public_repo" y pulsar en "Update Permissions" y seguir el asistente para asegurar que podemos hacer cambios

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
2) > git add . --> agrega todos los archivos nuevos de forma recursiva

Asi estamos preparados para hacer el commit a nuestro repositorio con el comando `git commit` que tiene el parametro `-m` para poner un mensaje al commit:
> git commit -m "commit inicial"

Ambos comandos (add y commit) se pueden integrar con el comando `git commit -am`, como:
> git commit -am "commit con mensaje"

Vamos a volver a hacer algún cambio y lo agregamos al staging. Si nos fijamos en la captura de la anterior operación `git add`, el sistema nos indica que podemos sacar un archivo del stage con `git reset HEAD` y el nombre del archivo. Lo probamos con `INFO.txt`:
1) `nano INFO.txt` --> agregar una nueva línea
2) `git status`
3) `git commit -am "algunos cambios"`
4) `git reset HEAD INFO.txt`
5) `git status`

Si en algun momento hemos hecho algun cambio y no estamos seguros, podemos devolver el archvio a su estado anterior con el comando `git checkout`:
> git checkout -- INFO.txt


## Histórico de operaciones en Git: logs
Con `git log` podemos ver el histórico de operaciones que hemos hecho:
> git log

Con `git help` log podemos ver las opciones que existen. Un ejemplo de una vista compacta y colorida sería:
> git log --oneline --graph --decorate --color


## Eliminar archivos del repositorio de Git
Imaginemos que uno de los archivos que ya están en el repositorio de git tras un commit no lo queremos allí. Podemos usar el comando `git rm` ("remove") y el nombre del archivo:
> git rm INFO.txt

Podemos observar que el status nos indica que el cambio ejecutado para el archivo a eliminar está en el staging. Para eliminarlo debemos hacer un nuevo commit:
> git status

> git add .

> git commit -am "Borrar archivo de texto"

> git push

* También se pueden usar los comandos estándares del sistema operativo para eliminar archivos, sin necesidad de usar `git rm`


## Ignorar archivos en Git
Ahora disponemos de un archivo que no queremos que se agregue nunca al repo, por ejemplo un archivo de registro con extension ".log". Podemos editar/crear el archivo `.gitignore`, en el que especificamos los archivos a ignorar en líneas independientes. Por ejemplo:
> nano .gitignore
```
*.log
```

Ahora hacemos un status y veremos el archivo .gitignore para agregar a staging:
> git status

> git add .

> git commit -m "Nuevo .gitignore"

> git push

El archivo `.gitignore` es obviado en GitHub y otra plataformas Git, por lo que aunque sea visible, no tiene acción ninguna.


## Repositorio remoto en GitHub
El comando `git remote` sirve para ver los repositorios remotos asociados. con la opción -v vemos la URL:
> git remote -v

Aunque ahora estamos trabajando sólos, lo lógico es solicitar los últimos cambios mediante un `git pull`, antes de enviar los nuestros con `git push`, para evitar conflictos con otros miembros del equipo. De modo que ejecutamos:
> git pull origin main

> git push origin main
* En documentos anteriores a 2021, se puede var la rama principal referenciada como "master" en vez de "main"

Isaac Valdespino(Invencible)