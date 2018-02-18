# pullRequestGuia

Describe cómo hacer un Pull Request

Tomado de [Hadley Wickhamh, R packages](http://r-pkgs.had.co.nz/git.html#git-pullreq).

## Fork

Desde tu usuario de **GitHub**, busca el repositorio externo en el que quieres colaborar. Una vez dentro del repositorio externo, busca el botón de `Fork`, presiónalo y escoge la cuenta a la cual vas a clonar el repositorio.

**IMAGEN FORK AQUI**

<<<<<<< HEAD
Una vez que **GitHub** ha clonado el repositorio externo a tu cuenta, abre el repositorio y busca el botón de `clone or download`, luego copia la dirección URL.

**IMAGEN FORK2 AQUI**

## Sincroniza el fork en un repositorio local
||||||| merged common ancestors
1. Sincronizar el repo con el original
=======
Una vez que **GitHub** ha clonado el repositorio externo a tu cuenta, abre el repositorio y busca el botón de `clone or download`, luego copia la dirección URL.
>>>>>>> 1418ad016903d896e5c98cad02c9af18f218250a

<<<<<<< HEAD
||||||| merged common ancestors
```
git remote add upstream git@github.com:<original-name>/<repo>.git
git fetch upstream
```
=======
**IMAGEN FORK2 AQUI**

## Sincroniza el fork en un repositorio local
>>>>>>> 1418ad016903d896e5c98cad02c9af18f218250a

<<<<<<< HEAD
Entra a **RStudio**. Luego, ve a  `New --> Project from Version Control`. Pega el URL que copiaste en el paso anterior, deja el nombre del repositorio por defecto, y escoge una carpeta para la copia local de los archivos.

El siguiente paso es muy importante. Tienes que decirle a **Git** que éste repositorio tiene un origen externo. Luego, que quieres volver a descargar todo desde el origen externo para mantener los archivos sincronizados. Para ello, ve a la consola **Git CMD**, y digita las siguientes líneas, cambiando los nombres correspondientes al repositorio externo.
||||||| merged common ancestors
4.  Luego, se pueden fusionar (*merge*) los cambios desde el repo original, hasta la copia local (*forked*) con:
=======

Entra a **RStudio**. Luego, ve a  `New --> Project from Version Control`. Pega el URL que copiaste en el paso anterior, deja el nombre del repositorio por defecto, y escoge una carpeta para la copia local de los archivos.

El siguiente paso es muy importante. Tienes que decirle a **Git** que éste repositorio tiene un origen externo. Luego, que quieres volver a descargar todo desde el origen externo para mantener los archivos sincronizados. Para ello, ve a la consola **Git CMD**, y digita las siguientes líneas, cambiando los nombres correspondientes al repositorio externo.
>>>>>>> 1418ad016903d896e5c98cad02c9af18f218250a

```
git remote add upstream git@github.com:<autor-original>/<repo-externo>.git

git fetch upstream

git merge upstream/master 
```

Ahora **Git** sabe del repositorio original, de manera que puedes estar al día con los cambios que haga el autor principal.  Cada vez que quieras actualizar tu repositorio local con el repositorio externo, debes decirle a **Git** que se ubique en una rama especial, digitando en el **Git CMD**:

```
git branch -u upstream/master  
```

Luego, haces un `pull`, con la particularidad de que estás tomando los archivos del repositorio externo y no del tuyo.

```
git checkout master
git pull
```

Se recomienda crear una rama (`<my-branch>`) para trabajar en un *pull request*; ya que, realmente no estás trabajando sobre la línea principal de desarrollo. Para mantener `<my-branch>` actualizada, digita en **Git CMD**:

```
git checkout <my-branch>
git merge master
```

Una vez que los cambios en tu rama local estén listos, y hayas decidido que tu contribución merece ser vista por el autor principal del repo, haz un *push*, y en la página de **GitHub** sigue los pasos para hacer un *Pull Request* al repo original.

**IMAGEN PULLREQUEST1**


**IMAGEN PULLREQUEST2**


# Actualizar el Fork

Correr **RStudio** como administrador.

En la consola de `git CMD`, indícale a **Git** que vas a leer desde el repositorio externo, para actualizar los cambios hechos por el autor principal (que deberían incluir aquellos que propusiste en un *pull request* si el autor los aceptó):

```
git branch -u upstream/master
```

Luego, descarga los cambios:

```
git pull
```

Luego, cambia la configuración para leer y escribir en el repositorio local, y *empuja* los cambios:

```
git branch -u origin/master

git push
```


## Borrar ramas antiguas


Una vez que se ha aceptado un *pull request*, ya no es necesario seguir trabajando en esa rama. Esta puede borrarse localmente al escribir `git branch -d <my-branch>`.  Y para borrarlo del repositorio en línea se utiliza:

```
 git push origin --delete <my-branch>
 ```
 
Siempre y cuado `origin` apunte al repositorio remoto. 