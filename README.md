# Guía para un *Pull Request*

Describe cómo hacer un Pull Request

Tomado de [Hadley Wickhamh, R packages](http://r-pkgs.had.co.nz/git.html#git-pullreq).

## General

Un *Pull request* es un procedimiento utilizado para colaborar en un repositorio que no te pertenece. Es decir, si colaboras en el repositorio de otra persona, y crees que los cambios que has hecho son relevantes para el trabajo del autor principal, puedes pedir que acepte tus cambios mediante un *pull request*. Para hacer un *pull request*, hay que seguir estos pasos:

1.  Hacer una copia personal del repositorio de otra persona (*Fork*).

1.  Sincronizar tu copia con el repositorio original externo.

1. Crear una rama para proponer tus cambios, y cuidar que siempre esté sincronizada con el original.

1. Subir a **GitHub** los cambios de tu rama, y crear un *Pull Request*

1. Esperar a que el autor del repositorio original revise los cambios y los acepte, o te proponga otra línea de acción.

1. Sincronizar todo de nuevo.


## Pasos para hacer un *Fork*

Un *Fork* es una copia **estática** del repositorio de otra persona. Es decir, para cualquier repositorio, puedes crear una copia para ti mismo, y modificarla (*si los permisos aplican*). También es utilizado para mantener una copia de un proyecto en tu disco duro, y mantenerla actualizada con los cambios del desarrollador principal, para lo cual, se debe sincronizar con el repositorio original.

Desde tu usuario de **GitHub**, busca el repositorio externo en el que quieres colaborar. Una vez dentro del repositorio externo, busca el botón de `Fork`, presiona y escoge la cuenta a la cual vas a clonar el repositorio.

![Fork, paso 1](https://github.com/dawidh15/dinPob/blob/master/figuras/Fork.png)

Una vez que **GitHub** ha clonado el repositorio externo a tu cuenta, abre el repositorio y busca el botón de `clone or download`, luego copia la dirección URL.

![Fork, paso 2](https://github.com/dawidh15/dinPob/blob/master/figuras/Fork2.png)

## Sincroniza el fork en un repositorio local

Antes de seguir, es importante determinar el tipo de conexión que utilizaremos. Hay dos tipos: el `HTTPS`, o el 'SSH'. Esto lo sabemos al momento de clonar la dirección del `Fork` (ver figura arriba).

- Si la dirección del `Fork` es algo como `https://github.com/<usuario>/<repositorio.git>`, entonces estamos ante un `HTTPS`.

- Por el contrario, si la dirección que vemos a la hora de clonar se ve como `git@github.com:<usuario>/<repositorio.git>`, estamos ante un `SSH`.

Una vez que estamos seguros del tipo de conexión que tenemos. Podemos proseguir.

Entra a **RStudio**. Luego, ve a  `New --> Project from Version Control`. Pega el URL que copiaste en el paso anterior (sea HTTPS o SSH), deja el nombre del repositorio por defecto, y escoge una carpeta para la copia local de los archivos.

## Dile a Git sobre la dirección original del repositorio

El siguiente paso es muy importante. Tienes que decirle a **Git** que éste repositorio viene de otra persona (este es el repositorio original que no te pertenece, y se conoce como **upstream**). Para ello, ve a la consola **Git CMD**, y digita las siguientes líneas, cambiando los nombres correspondientes al repositorio externo.


**Para HTTPS**

```
git remote add upstream https://github.com/<usuario>/<repositorio.git>

```

**Para SSH**

```
git remote add upstream git@github.com:<autor-original>/<repo-externo>.git
```

Ahora **Git** sabe del repositorio original, de manera que puedes estar al día con los cambios que haga el autor principal. 

Para verificar que todo esta bien, digita `git remote -v`. Deberías ver la dirección del **origin** (que se refiere a la copia remota de tu `Fork`), y la dirección del **upstream**.

Si hay algo mal con las direcciones del **upstream**, debes borrar primero las direcciones guardadas: `git remote remove upstream` . Y volver a introducir la dirección con `git add upstream`...


## Trabaja en una rama alternativa

La línea de desarrollo principal le pertenece al dueño del repositorio (**upstream**); por tanto, tú nunca estás realizando un trabajo sobre el tronco principal del proyecto, sino que trabajas en ramas del proyecto. Para crear una rama desde **RStudio** sigue los pasos de la figura de abajo:

IMAGEN new branch

Una vez que haz creado la rama, puedes hacer todos los cambios que quieras en el documento. Hacer `commits`, y subir los cambios a tu copia remota (**origin**).

## Haz un **Pull Request**

Uno de los principios de Git y la colaboración en línea, es que todos los colaboradores siempre deben tener los archivos actualizados entre sí. Como la línea de desarrollo principal le pertenece al dueño del repositorio externo (**upstream**), tu copia (`Fork`) debe estar siempre al día. De hecho, **Git** no te deja hacer un *Pull Request* si no estás sincronizado. Lo más sencillo es abrir una terminal de **Git CMD** y digitar:

- `checkout master` (cambia de la rama de trabajo, al master local)

- `git fetch upstream` (trae los cambios del desarrollador principal, a tu rama local)

- `git merge upstream/master`  (fusiona los cambios del desarrollador principal, con tu computador local)

- En este punto, si hay conflictos, deben ser resueltos con un `commit`.

Si tienes suficientes cambios importantes, y quieres pedirle al dueño del **upstream** que incorpore tus cambios, abre una terminal de **Git CMD** y digita:

- `git checkout -b <my_rama>`

- `git push --set-upstream origin <my_rama>`

- Luego, en **GitHub.com** busca la rama en tu repositorio. Y encuentra el botón de *Crear un Pull Request*.

## Después de un Pull Request

Una vez que el desarrollador principal ha aceptado tus cambios, y los ha incorporado a la línea principal (**upstream**), debes actualizar tu repositorio local y tu repositorio remoto. Abre una terminal de **Git CMD**.


- `checkout master` (cambia de la rama de trabajo, al master local)

- `git fetch upstream` (trae los cambios del desarrollador principal, a tu rama local)

- `git merge upstream/master`  (fusiona los cambios del desarrollador principal, con tu computador local)

- En este punto, si hay conflictos, deben ser resueltos con un `commit`.

- `git push origin` (sincroniza tu **origin**)

- `git checkout <mi_rama>` (cambia a tu rama de trabajo)

-`git merge master` (fusiona tu rama con el master, es decir, incorpora los cambios de la línea de desarrollo principal)

- `git push -u origin <mi_rama>` (sincroniza tu rama en el **origin**)

Si en este punto, ya no necesitas seguir trabajando en tu rama, puedes borrarla con:

- `git checkout master`

-`git branch -d <mi_rama>` (borra la rama localmente, en tu computador)

- `git push origin --delete <mi_rama>` (borra la rama en el **origin**)

![New Pull request, paso 1](https://github.com/dawidh15/dinPob/blob/master/figuras/PullRequest1.png)


![New Pull request, paso 2](https://github.com/dawidh15/dinPob/blob/master/figuras/PullRequest2.png)


