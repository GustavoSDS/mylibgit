# CURSO DE GIT EN BASE A LA DOCS

- **File Config global**
    > git config --global -e

> git init

## GUARDANDO CAMBIOS EN EL REPOSITORIO

1. _**Revisando el Estado de tus Archivos**_

    - Ver el estado de los archivos
        > git status
    - Ver el estado abreviado
        > git status -s / --short
    - Ver detalles de la rama
        > git stutus -b / --branch

2. _**Rastrear Archivos Nuevos**_

    - Rastrear archivo
        > git add name-file/directory
    - Rastrear y seguir cambios
        > git commit -a -m "Message for commit"
3. _**Ver los Cambios Preparados y No Preparados**_

    - Ver qué has cambiado pero aun no has preparado
        > git diff | git diff name-file
    - ver lo que has preparado y será incluido en la próxima confirmación
        > git diff --staged/cached
4. _**Confirmar tus Cambios**_

    - La forma más sencilla de confirmar los cambios ya preparados
        > git commit -m "Message for commit"
    - Para obtener una forma más explícita de recordar qué has modificado
        > git commit -m "Message for commit" -v
5. _**Saltar el Área de Preparación**_

   - Si quieres saltarte el área de preparación
        > git commit -a -m "Message for commit"
6. _**Eliminar Archivos**_

    - Eliminar el archivo de tu directorio de trabajo de manera que no aparezca la próxima vez como un archivo no rastreado
        > git rm -r --cached name-file/directory | git rm log/\*.log
7. _**Cambiar el Nombre de los Archivos**_

    - Si quieres renombrar un archivo en Git
        >  git mv file_from file_to

## VER HISTORIAL DE CONFIRMACIONES

> **git log**

- muestra las diferencias introducidas en cada confirmación
    > git log -p
- muestra únicamente las dos últimas entradas del historial
    > git log -p -2
- Imprime cada confirmación en una única línea
    > git log --oneline
- Ver algunas estadísticas de cada confirmación
    > git log --stat
- Modifica el formato de la salida
    > git log --pretty
- Añade un pequeño gráfico ASCII mostrando tu historial de ramificaciones y uniones
    > git log --pretty=format:"%h %s" --graph
    > git log --pretty=format:"%h %s" --graph -20

- Muestra solamente la línea de resumen de la opción --stat
    > git log --shortstat
- Muestra la lista de archivos afectados
    > git log --name-only
- Muestra la lista de archivos afectados, indicando además si fueron añadidos, modificados o eliminados.
    > git log --name-status
- Muestra solamente los primeros caracteres de la suma SHA-1, en vez de los 40 caracteres de que se compone
    > git log abbrev-commit
- Muestra la fecha en formato relativo (por ejemplo, “2 weeks ago” (“hace 2 semanas”)) en lugar del formato completo
    > git log --relative-date
- Muestra un gráfico ASCII con la historia de ramificaciones y uniones
    > git log --graph

### Limitar la Salida del Historial

- Este comando lista todas las confirmaciones que cumplan las especificaciones
    > git log --sice=2.weeks
    > git log --since=1.days
    > git log --author=GustavoSDS
    > git log --grep="new line"
    > git log --author="name autor" --grep="palabra clave" --all-match
    > git log --committer="name committ"
    > git log --after|until|before

## DESHACER COSAS

- Si quieres rehacer la confirmación, puedes reconfirmar con la opción --amend
    > git commit --amend

- Deshacer un Archivo Preparado
    > git reset HEAD name-file
    > git reset --hard HEAD name-file
- Deshacer un Archivo Modificado
    > git checkout -- name-file

## ETIQUETADO (Version)

- Listar Tus Etiquetas
    > git tag
    > git tag -l "version-search"/"1.6.*"
- Crear Etiquetas
  - Etiquetas Anotadas
    > git tag -a v1.4 -m "my version 1.4"
  - Etiquetas ligeras
    > git tag v1.4-lw
- Mostrar detalles de la version
    > git show vnumber
- Etiquetado Tardío
    > git tag -a v1.2 checksum
- Compartir Etiquetas
    > git push origin vtag
    > git push origin --tags //send all tags
- Sacar una Etiqueta
    > git checkout -b version2 v2.0.0

## ALIAS EN GIT

> git config --global alias.co checkout
> git config --global alias.br branch
> git config --global alias.ci commit
> git config --global alias.st status

## RAMIFICACIONES EN GIT

### Crear una Rama Nueva

> git branch name-branch

- Mostrar a donde apunta cada rama
    > git log --oneline --decorate
- Cambiar de Rama
    > git checkout name-branch

### Procedimientos Básicos para Ramificar y Fusionar

- Procedimientos Básicos de Ramificación
    > git checkout -b iss53 //crear y cambiar de rama
- Fusionar ramas
    > git merge name-rama-a-fusionar
- Eliminar ramas
    > git branch -d name-rama

## GESTION DE RAMAS

- git branch
- git branch -v  
- git branch --merged //ver ramas fusionadas con la actual
- git branch --no-merged // "" no "" con la actual

## FLUJOS DE TRABAJO RAMIFICADOS

_**Ramas de Largo Recorrido**_

- Examples
    > git checkout -b develop
    > git checkout -b topic
    > git checkout -b proposed

_**Ramas Puntuales**_

- Examples
    > git checkout -b iss53
    > git checkout -b iss91
    > git checkout -b iss92v2
    > git checkout -b dumbidea

## RAMAS REMOTAS

### Trabajar con Remotos

- Ver tus romotos
    > git remote
    > git remote -v
- Añadir Repositorios Remotos
    > git remote add [name] [URL]
- Publicar
    > git push [nombre-remoto] [nombre-rama]
    > git push -u [nombre-remoto] [nombre-rama]
    > git push -u -f [origin] [git@github.com:gsds/project.git]
    > git remote set-url origin https_link_to_repository
- Traer y Combinar Remotos
    > git fetch [remote-name] -> traer datos del remoto
    > git pull [remote-name]  -> combinar remoto con local
    > git clone [remote-name] -> clonar un remot
- Credencial
    > git config --global credential.helper cache
- Inspeccionar un Remoto
    > git remote show [nombre-remote]
- Eliminar y Renombrar Remotos
    > git remote rename [old-name] [new-name]
    > git remote rm [remote-name]
