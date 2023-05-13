# Course the git in terminal

## Estoy aprendiendo sobre los estados

> - **Staged**
> - **Modified**
> - **Unmodified**
> - **Untraked**

### Guardando cambios en el repositorio

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

### Ver historial de confirmaciones

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

#### Limitar la Salida del Historial

- Este comando lista todas las confirmaciones que cumplan las especificaciones
    > git log --sice=2.weeks
    > git log --since=1.days
    > git log --author=GustavoSDS
    > git log --grep="new line"
    > git log --author="name autor" --grep="palabra clave" --all-match
    > git log --committer="name committ"
    > git log --after|until|before

### Deshacer Cosas

- Si quieres rehacer la confirmación, puedes reconfirmar con la opción --amend
    > git commit --amend

- Deshacer un Archivo Preparado
    > git reset HEAD name-file
    > git reset --hard HEAD name-file
