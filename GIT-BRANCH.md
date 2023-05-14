# RAMIFICACIONES EN GIT

## Crear una Rama Nueva

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

### Hacer Seguimiento a las Ramas

- Preparar otras ramas de seguimiento si deseas tener unas que sigan ramas de otros remotos
    > git checkout --track origin/[name-rama]
- Preparar una rama local con un nombre distinto a la del remoto
    >  git checkout -b [name-rama] origin/[name-rama]
- Cambiar la rama a la que le haces seguimiento
    > git branch -u origin/[name-rama]
- Ver las ramas de seguimiento que tienes asignadas
    > git branch --v
- Si quieres tener los cambios por delante y por detrás
actualizados
    > git fetch --all; git branch -vv

### Traer y Fusionar

- > git pull origin [name-rama]

### Eliminar Ramas Remotas

- > git push origin -delete [name-rama]

## REORGANIZAR EL TRABAJO REALIZADO

### Reorganización Básica

- > git rebase [name-rama1]
  > git merge [name-rama2]

### Algunas Reorganizaciones Interesantes

- Imagina que decides incorporar tus cambios del lado cliente sobre el proyecto principal para hacer un lanzamiento de versión; pero no quieres lanzar aún los cambios del lado servidor porque no están aún suficientemente probados
    > git rebase --onto main [name-rama1] [name-rama2]
    > git merge [name-rama2]
    > git config --global pull.rebase true
