# Curso Git | GitHub

## Introducción

### Acerca del control de versiones

Al momento de desarrollar es importante poder llevar un registro histórico de todos los cambios generados por todos los involucrados en el proyecto, en eso radica la popularidad de los controladores de versiones de hoy en día. Nos permiten administrar cualquier desarrollo de software de una manera eficaz y rápida.

El correcto uso de esta tecnología puede ser un valioso aliado, ya que nos ahorra el hecho que tengamos que hacer nosotros mismos respaldos de archivos que a lo mejor nos olvidemos donde estén o modifiquemos en algún lugar que no sea el correcto, así como nos ofrece movernos libremente entre el histórico de todos los archivos. También funciona perfecto para equipos de gran tamaña como también para quien trabaja en solitario por su flexibilidad en el flujo de trabajo.

### Git, una breve explicación

> _Git fue creado pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente, es decir Git nos proporciona las herramientas para desarrollar un trabajo en equipo de manera inteligente y rápida y por trabajo nos referimos a algún software o página que implique código el cual necesitemos hacerlo con un grupo de personas._
> -Andrés en [Codigo Facilito](https://codigofacilito.com/articulos/que-es-git).

Git es un sistema de control de versiones distribuido, es decir, que existe el código fuente en el servidor y en los equipos donde se guarda el proyecto, siendo completamente independiente del servicio de alojamiento principal.

La gran ventaja que nos brinda es la seguridad de que si algún día llegará a corromperse algunos archivos en el servidor o alguien borrará el proyecto principal por accidente, cualquiera que tuviera una copia del programa antes de que pasará una de las situaciones anteriormente planteadas pudiese ser el salvador del equipo pudiendo re-subir el repositorio y seguiría el curso del desarrollo como si no hubiera pasado nada.  

![Control de versiones distribuido][git-distribuido]

### Configuración

#### Primera configuración

Antes que nada, es necesario hacer unas configuraciones a git para poder identificar al usuario y correo para saber quien esta interactuando en los repositorios.

```shell
git config --global user.name = ["nombre-usuario"]
git config --global user.email = ["correo"]
```

#### Alias

Los alias sirven para acortar ciertos comandos que son difíciles de recordar y cansados de teclear, por ello es necesario declararlos de manera global para que en cualquier momento se pueda utilizar.

```shell
git config --global alias.<alias> ["comando-con-banderas"]
```

Los alias que más ocupo son:

```shell
git config --global alias.lg "log --oneline --decorate --all --graph"
git config --global alias.s "status -s -b"
```

<!-- https://styde.net/crear-alias-de-comandos-con-git/ -->

#### Formateo y espacios de los archivos

Cuando se trabaja en equipo o en solitario pero en dos sistemas operativos distintos es común que se presente el error del como esta formateado los archivos, ya que Windows, Linux y OSX manejan de distinta manera los caracteres de una nueva linea.

```shell
git config --global core.autocrlf true # Windows
git config --global core.autocrlf input # Linux & OSX
```

Si no se configura esto, puede arrojar la siguiente advertencia ``warning: LF will be replaced by CRLF in [FILE_NAME]. The file will have its original line endings in your working directory``, en donde se dispara cuando se están haciendo los commits.

#### Conexión con SSH

- Generar llave
- Testear
- Configurar llave Github

<!-- https://help.github.com/en/articles/connecting-to-github-with-ssh -->

#### Autentificación de doble factor

#### Manipular archivo de configuración

Muchas de las veces es necesario consultar nuestras configuraciones globales para identificar que variables esta tomando nuestro control de versiones.

```shell
git config --global -l
```

De igual manera, aveces, se tendrá la necesidad de modificar las configuraciones de una manera sencilla y rápida.

```shell
git config --global -e
```

## Fundamentos 

### Generando un repositorio

Para poder manejar cualquier proyecto con git es necesario tener una carpeta de **.git**, está es el encargada de llevar todo el control de nuestros archivos y el espacio tiempo en el que se hicieron los cambios.

#### Inicializando un repositorio

Si el proyecto no ha tenido ninguna intervención con git es necesario inicializarlo para que empiece a llevar el control de todos los archivos.

```shell
git init
```

Se recomienda que después inicializar el proyecto se agregue un archivo llamado _README.md_ y se haga el primer commit, ya que este archivo en GitHub o GitLab se muestra en la página principal del proyecto y sirve para mostrar una breve descripción del repositorio o una carta de presentación o simplemente información necesaria para entender lo que se desarrolló.

```shell
git add README.md
git commit -m "Initial commit"
```

#### Clonando un repositorio

Si deseas modificar o contribuir a un repositorio ya existente es necesario descargarlo en tu computadora, con esto tendrás una copia idéntica a la del servidor y así tienes la posibilidad de modificar todos los archivos como gustes.

```shell
git clone <url>
git clone <url> <nombre-del-proyecto>
```

Git permite clonar proyectos de dos maneras diferentes. La primera es através del protocolo HTTTPS pero también se puede usar el protocolo SSH. Cabe aclarar que la segunda opción tiene un filtro de seguridad para que identifique al usuario sin exponer datos confidenciales del desarrollador.

### Cambios en el repositorio

#### Revisar los cambios en el proyecto ~ status

El estado nos muestra todas las rutas que tienen diferencias entre el archivo **index** y la posición actual de **HEAD**, las rutas que tienen diferencias entre la rama que se esta trabajando y el archivo **index** y las rutas de la rama en la que se esta trabajando que no están siendo seguidas por Git y que no están siendo ignoradas por el archivo **.gitignore**. Esto quiere decir que se visualizará el estado de todos los archivos que contengan cambios que no hayan sigo archivados con un commit en el espacio de trabajo.

Para poder identificar si hubo algún tipo de cambio, se agrego nuevos archivos o carpetas, es necesario utilizar **status**, que nos permite identificarlo de una manera gráfica lo anterior dicho, ademas identificando si esta en el _stage_.

```shell
git status
```

Una forma de abreviar la salida del comando y sea más visible lo que esta pasando en el stage, es poniendole la bandera de **short**.

```shell
git status -s
```

Para poder conocer en el comando con que rama se está trabajando también pero de la forma acortada es agregandole la bandera de **branch**.

```shell
git status -s -b
```

#### Agregar archivos al escenario ~ stage

Staging area o Index es una especie de área de almacenamiento en donde se colocan los contenidos que se deben confirmar en el commit.

Hay varias maneras con las cuales se puede filtrar que archivos o carpetas se desea agregar al stage, esto ocasionará que en la búsqueda de errores a través del tiempo sea más rápida y visible.

Para agregar un único archivo:

```shell
git add <nombre-del-archivo>
git add ejemplo.html # Ejemplo
```

Para agregar muchos archivos a la vez:

```shell
git add <archivo-1>...<archivo-n>
git add ejemplo.html css/style.css js/app.js # Ejemplo
```

Para agregar una carpeta en especifico con todo su contenido:

```shell
git add <nombre-carpeta>/
git add js/ # Ejemplo
```

Para agregar todos los archivos con un tipo de extensión en la direccion actual:

```shell
git add *.<nombre-tipo-archivo>
git add *.jpg # Ejemplo
```

Para agregar todos los archivos con un tipo de extensión en todo el proyecto:

```shell
git add "*.<nombre del tipo de archivo>"
git add "*.jpg"
```

Para agregar todos los archivos con un tipo de extensión en la carpeta especificada:

```shell
git add <nombre de carpeta>/*.<nombre del tipo de archivo>
git add img/*.jpg # Ejemplo
```

Para agregar todos excluyendo ciertos archivos o carpetas con filtro:

```shell
git add .
git reset <filtro>
git reset  js/ css/ favicon.ico # Ejemplo
```

#### Ignorar archivos ~ gitignore

A veces, tendrás algún tipo de archivo que no quieres que Git añada automáticamente o más aun, que ni siquiera quieras que aparezca como no rastreado.Este suele ser el caso de archivos generados automáticamente como trazas
o archivos creados por tu sistema de compilación. 

El archivo ``.gitignore`` especifica todos los archivos que no se podrán rastrear por git. Los archivos que ya hayan sido rastreados no sufrirán los cambios. En cada linea de este archivo se especifica un patrón. Cuando Git decide que ignorar, normalmente checa todos los patrones alojados en estos archivos.

```shell
touch .gitignore
```

Para ahorrar un poco de tiempo se puede recurrir a la pagina web de [gitignore.io](https://www.gitignore.io/). Esta web nos ayuda a configurar de una manera fácil y rápida dependiendo del proyecto el archivo.

#### Checar diferencias entre el stage y el commit ~ diff

El diferenciador nos sirve para responder estas dos preguntas: ¿Qué se ha cambiado pero aun no se pasa al stage? y ¿Qué se ha preparado y está listo para confirmar? A pesar de que ``git status`` responde a estas preguntas de forma muy general listando el nombre de los archivos, `git diff` te muestra las líneas exactas que fueron añadidas y eliminadas, es decir, desglosa con mayor exactitud que se esta modificando.

Al identificar los cambios, se puede llegar a saber en que se estaba trabajando la ultima vez que se modificaron los cambios

```shell
git diff
```

Con el anterior comando es imposible conocer los cambios entre HEAD y lo que hay en el stage, por ello hay una bandera especial que se encarga de eso.

```shell
git diff --staged
```

#### Haciendo una captura del tiempo ~ commit

Para poder guardar todos los cambios que se generaron en los archivos que estaban en el stage, es necesario validarlo con un **commit**. Esto permitirá que se genere un registro de ese punto en el tiempo.

Lo más adecuado a la hora de estar trabajando en un proyecto real es simplificar las tareas para que el desarrollo sea más ágil y alcanzable y esto se tiene que ver reflejado en el nombramiento de los commits.

Se guardará el apuntador de los archivos que estaban en el _stage_, unos metadatos con el autor y el mensaje explicativo de lo que sucedió en ese punto del tiempo.

```shell
git commit -m <mensaje>
git commit -m "Primer commit"
```

Existe una bandera para **commit** que hace que todos los archivos que hayan sido rastreados por el repositorio y hayan sufrido cambios sean agregados directamente al stage y se guarde a un apuntador del tiempo.

```shell
git commit -am <mensaje>
git commit -am "Se actualizo index.html y los estilos"
```

El apuntador de HEAD es el que se encuentra siempre en el último commit en la linea del tiempo.

#### Cambiar el nombre de archivos ~ mv

Git no rastrea explícitamente los cambios de nombre en archivos. Si se renombra un archivo en Git, no se guardará ningún metadato que indique que se cambio. Sin embargo, Git es bastante listo como para detectar estos cambios luego que los has hecho.

```shell
git mv <nombre-actual> <nombre-nuevo>
```

Sin embargo, eso es equivalente a ejecutar los siguientes comandos:

```shell
git rm <nombre-archivo>
git add <nombre-archivo>
```

#### Eliminar archivos ~ rm

Para eliminar archivos de Git, se debe eliminar de los archivos rastreados (o mejor dicho, eliminarlos del área de preparación) y luego confirmar. Para ello existe el siguiente comando, que además elimina el archivo del directorio de trabajo de manera que no aparezca la próxima vez como un archivo no rastreado.

```shell
git rm <nombre>
```

Otra cosa que se puede hacer es mantener ciertos archivos en tu directorio de trabajo pero eliminarlo del área de preparación. En otras palabras, se quisiera mantener el archivo en tu disco duro pero sin que Git lo siga rastreando. Esto puede ser particularmente útil si olvidaste añadir algo en tu archivo `.gitignore` y lo preparaste accidentalmente. 

```shell
git rm --cached README
```

### Checar el historial de los commits ~ log

Sirve para mostrar el historial de los commits hechos localmente.

```shell
git log
```

Para tener las estadísticas sobre los archivos modificados en cada uno de los commits es necesario agregarle una bandera al comando.

```shell
git log --stat
```

Para mostrar solamente las últimas n commits que se hicieron es necesario combinar una bandera con el número deseado.

```shell
git log -<numero>
git log -2
```

Para mostrar todos los commits respecto a ciertas fechas especificas es necesario indicar unas banderas especiales en las que se necesita poner las fechas exactas.

```shell
git log --after=["fecha"] --before=["fecha"]
git log --after="2019-02-15" --before="2019-02-20" 
git log --after="2019-02-12T16:00:00-00:00"
git log --after="1 month ago"
git log --after="2 weeks 3 days 2 hours 30 minutes 59 seconds ago"
```

Para tener una mejor presentación de los datos en donde se despliega en una sola linea con el hash, el nombre del commit y en donde se encuentra el _HEAD_ es necesario agregarle una bandera al comando.

```shell
git log --oneline
```

Para poder visualizar todos los cambios que se fueron generando de una manera gráfica es necesario agregarle dos banderas al comando para que se pueda mover entre branches y merges.

```shell
git log --graph --decorate
```

Cabe destacar que las banderas del log antes mencionados se pueden combinar para checar de una mejor manera lo que esta pasando al proyecto, es decisión de cada uno elegir cual es la más funcional para cada uno.

### Deshacer cosas importantes ~ reset

Para poder modificar el nombre del ultimo commit generado es necesario utilizar el siguiente comando.

```shell
git commit --amend
```

Para poder eliminar un archivo del stage es necesario ocupar un comando especial

```shell
git reset HEAD <nombre-archivo>
```

Para poder traer de vuelta al stage todos los cambios del penúltima commit es necesario ocupar un reset con una bandera especial del commit que se quiera actualizar, en este caso cuando se ocupa el HEAD^ y con ello se puede hacer de nuevo el commit con un nuevo nombre

```shell
git reset --soft HEAD^
```

Para poder dejar un archivo como estaba en el ultimo commit es necesario ejecutar un comando que pudiera ser muy delicado si hay cambios importantes que no se encuentren en el stage, no se podrá recuperar los datos una vez ejecutado este comando.

```shell
git checkout -- <nombre-archivo>
```

El siguiente comando sirve para revertir los cambios y regresar los archivos al ultimo commit de todos los cambios que se realizaron y que no se encuentren en el stage.

```shell
git checkout -- .
```

<!--Redactar esto-->
Cuando se esta viajando en el tiempo es posible estar sin eliminar los cambios que se hicieron a traves de la bandera soft

```shell
git reset --soft <hash del commit>
```

Para poder ir a un punto de la historia y los commits adelante de donde se viajara se pondran afuera del escenario y aun contendra las modificaciones

```shell
git reset --mixed <hash del commit>
```

Para eliminar los commits delante del que esta es necesario utilizar el siguiente comando

```shell
git reset --hard <hash del commit>
```

Para identificar todos los movimientos que se hicieron apesar de que hayan sido eliminador por un reset hard es posible recuperarlo obteniendo su hash en la tabla de todos los cambios que se hicieron

```shell
git reflog
git reset --hard <hash del commit>
```

<!-- https://platzi.com/discusiones/1170-git-github/321-53433eef-e76d-4620-9bad-103597d1d943/
https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard -->

### Proyectos remotos

Los repositorios remotos son versiones de tu proyecto que se encuentran alojados en Internet o en algún punto de la red. Puedes tener varios, cada uno de los cuales puede ser de sólo lectura, o de lectura/escritura, según los permisos que tengas. Colaborar con otros implica gestionar estos repositorios remotos, y mandar (push) y recibir (pull) datos de ellos cuando necesites compartir cosas.

Esta configuracion es para identificarte como usuario de github en git

```shell
git push -u origin master
```

#### Ver 

#### Añadir ~ add

```shell
git remote add <nombre-repositorio> <url-repositorio>
git remote add upstream <url> #Por convención es upstream
```



#### Comparar ~ fetch

#### Recibir~ pull

#### Enviar ~ push

#### Inspeccionar ~ show

#### Modificar ~ rename

#### Eliminar ~ rm

```
git branch -D <nombre-rama> # Localmente
git push origin:<nombre-rama> # Desde local a github
git remote prune origin # Eliminar todas las que ya no se encuentran en github
```



### Etiquetas ~ tag

Git tiene la habilidad de etiquetar puntos específicos en la historia como importantes. Generalmente la gente usa esta funcionalidad para marcar puntos donde se ha lanzado alguna versión (v1.0, y así sucesivamente).

<!-- Para revisar como versionar https://semver.org/ -->

Para ver todos los tags

```shell
git tag 
```

Para crear un tag es necesario

```shell
git tag <nombre del tag>
git tag -a <version> -m ["mensaje"]
git tag -a <version> <hash del commit al que se quiera poner tag> -m ["mensaje"]
```

Para borrar un tag es necesario

```shell
git tag -d <nombre del tag>
```

Para ver todos los cambios hechos en ese punto de la historia con el tag

```shell
git show <nombre del tag>
```

Por defecto, el comando `git push` no transfiere las etiquetas a los servidores remotos. Se debe de enviar las etiquetas de forma explícita al servidor luego de que se hayas creado.

```shell
git push origin <nombre-etiqueta>
```

Si se quiere enviar varias etiquetas a la vez, se puede usar una bandera especial con el comando de push. Se enviarán todas las etiquetas que aun no existan en él.

```shell
git push origin --tags
```

<!-- Tambien hay release https://help.github.com/en/articles/about-releases -->

### Pedir ayuda ~ help

Es muy fácil perdernos entre tanto que aprender y por ello git nos puede proporcionar una guía bastante útil cuando la necesitemos respecto a los comandos que existen, por ello es importante conocer las diferentes maneras de pedir ayuda.

```shell
git help
git help <comando>
git <comando> --help
```

## Ramificaciones

### Acerca de ramas

Una rama de git es simplemente un apuntador ubicado en uno de los diferentes commits. La rama por defecto es la master. En cada commit que realicemos, la rama irá avanzando automaticamente. Por default, la rama que se utiliza es la master.

<!--![Apuntadores de la branch][git-branch]-->

Cuando se manejan distintas ramas se crea un nuevo apuntador para que se pueda mover libremente en ella, y se comportara de la misma manera como en la master, en donde _Head_ será el apuntador donde nos dira la rama con la que estemos trabajando.

<!--![Apuntador Head en la separación de la branch][git-branch-create]-->

Para checar todas las ramas existentes y en cual se está

```shell
git branch
```

Para moverse entre ramas

```shell
git checkout <nombre-rama>
```

Para poder crear nuevas ramas es necesario ocupar el comando

```shell
git branch <nombre-branch>
```

Para poder crear nuevas ramas y al mismo tiempo moverse en ellas es necesario ocupar el comando

```shell
git checkout -b <nombre-branch>
```

Para checar diferencias entre las ramas

```shell
git dif <nombre-branch-uno> <nombre-branch-dos>
```

Para eliminar una rama

```shell
git branch -d <nombre de la rama>
```

El proceso de fusionado se conoce como merge y puede llegar a ser muy simple o más complejo si se encuentran cambios que Git no pueda procesar de manera automática. Git para procesar los merge usa un antecesor común y comprueba los cambios que se han introducido al proyecto desde entonces, combinando el código de ambas ramas. 

Para poder hacer cualquier merge es necesario estar en la rama en la cual se quieran agregar todos los cambios de la otra rama.

### Procedimientos básicos para ramificar y fusionar

### Gestionar ramas

#### Fast-fordward

Git simplemente mueve el puntero hacia adelante para fusionar los cambios de la rama secundaria a la principal. Para expresarlo de otra manera, cuando intenta un merge  con un commit con otro al que se puede llegar siguiendo el historial del primer commit, Git simplifica las cosas moviendo el puntero hacia adelante porque no hay archivos que se hayan modificado en las dos ramas al mismo tiempo.

```shell
git merge <rama-a-unir>
```

#### Merge commit

En lugar de simplemente mover el puntero de la rama hacia adelante, Git crea una nueva instantánea que resulta de esta combinación de tres vías y crea automáticamente una nueva confirmación que apunta a ella. Esto se conoce como un merge commit, y es especial porque tiene más de un padre.

```shell
git merge <rama-a-unir>
```

#### Merge conflicts

En algunas ocasiones, los procesos de fusión no suelen ser fluidos. Si hay modificaciones dispares en una misma porción de un mismo archivo en las dos ramas distintas que pretendes fusionar, Git no será capaz de fusionarlas directamente.Si se cambia la misma parte del mismo archivo de manera diferente en las dos ramas que está fusionando, Git no podrá combinarlas de manera limpia y causará problemas.

Git no crea automáticamente una nueva fusión confirmada (merge commit). Sino que hace una pausa en el proceso, esperando a que tu resuelvas el conflicto. Para ver qué archivos permanecen sin fusionar en un determinado momento conflictivo de una fusión, puedes usar el comando ``git status``.

Primero se debe de hacer el merge y despues el commit de la resolución del conflicto.

```shell
git merge <rama-a-unir>
git commit -am ["Mensaje de resolución de conflicto"]
```



### Flujos de trabajos

### Ramas remotas

### Reorganizar el trabajo

## Stash

Normalmente  el espacio de trabajo suele estar en un estado inconsistente. Pero puede  que se necesite cambiar de rama durante un breve tiempo para ponerse a  trabajar en algún otro tema urgente. Esto plantea el problema de  confirmar cambios en un trabajo medio hecho, simplemente para poder  volver a ese punto más tarde. 

Este comando de guardado rápido (stashing) toma el estado del espacio  de trabajo, con todas las modificaciones en los archivos bajo control  de cambios, y lo guarda en una pila provisional. Desde allí, se podrán  recuperar posteriormente y volverlas a aplicar de nuevo sobre el espacio  de trabajo.

Para almacenar los cambios de todo el directorio es necesario utilizar el siguiente comando.

```shell
git stash
```

Para listar todos la lista de los stash

```shell
git stash list
```

Para regresar el ultimo stash es necesario utilizar el comando, cabe destacar que si se utiliza pop se eliminara el stash de la lista y si se utiliza apply ahí seguirá.

```shell
git stash [pop|apply]
```

O para restaurar un  stash en especifico

```shell
git stash apply stash@{<numero-stage>}
```

Para eliminar un stage en especifico es necesario el siguiente comando

```shell
git stash drop stash@{<numero-stash>}
```

O para eliminar la primera encontrada

```shell
git stash drop
```

O para eliminar todas las entradas

```shell
git stash clear
```

Cuando se encuentre conflictos a la hora de hacer el merge del stash con el index de tu repositorio es necesario corregir manualmente el error y hacer un commit para seguir adelante, pero sin antes olvidar checar si se elimino el stash que se uso.

```shell
git stash [pop|apply]
git commit -am ["Mensaje de resolucion de conflicto"]
git stage drop
```

Hay algunas banderas que son importantes para stage que son las que guardan todo menos lo que esta en el stage y los que incluyen guardar los cambios incluso en los archivos que no tienen un seguimiento

```shell
git stash push --keep-index
git stash push --include-untracked
```

Para mostrar todas las modificaciones de los stage se pueden hacer de dos maneras diferentes

```shell
git stash list --stat
git show stash
git show stash@{<numero-stash>}
```

Para agregar mensajes a los stash 

```
git stash push -m ["Mensaje"]
```

<!-- https://git-scm.com/book/es/v1/Las-herramientas-de-Git-Guardado-r%C3%A1pido-provisional -->

## Rebase

Es el proceso de mover o combinar una secuencia de commits a una nueva base de commits. La modificación de rebase es más útil y se visualiza fácilmente en el contexto de un flujo de trabajo de ramificación de características.

- Ordenar commits
- Corregir mensajes de commits
- Unir commits
- Separar commits

### Update branch

Sirve para mover los commits y a un tiempo para que no tenga conflictos a la hora de hacer merge entre las ramas

Primero nos vamos a la rama que queremos mover, hacemos el rebase, nos regresamos a la rama original y hacemos el merge sin ningún problema

```shell
git checkout <nombre-rama-a-ir>
git rebase <nombre-rama-a-mover>
git checkout <nombre-roriginal>
git merge <rama-a-combinar>
```



### Squash

Sirve para unir todos los commits en uno solo y poder renombrar en un solo commit, es necesario utilizar un rebase interactivo

```shell
git rebase -i <patron-de-commits>
git rebase -i HEAD~4 #Ejemplo
```

Y es necesario utilizar la letra s o squash en los commits  que se quieren unir en el editor de vim.

### Reword

Sirve para modificar el nombre del commit, es necesario utilizar un rebase interactivo.

```shell
git rebase -i <patron-de-commits>
git rebase -i HEAD~1 #Ejemplo
```

Y es necesario utilizar la letra r o reword en los commits  que se quieren modificar en el editor de vim.

Y por si las dudas, se ejecuta el siguiente comando para que no cree otra rama

```shell
git checkout <rama>
git checkout master #Ejemplo
```

### Edit

Sirve para modificar los archivos del commit, es necesario utilizar un rebase interactivo.

```shell
git rebase -i <patron-de-commits>
git rebase -i HEAD^ #Ejemplo
```

Y es necesario utilizar la letra e o edit en los commits  que se quieren modificar en el editor de vim.

Para modificar los archivos es necesario dejarlos como estaban antes de hacer el commit

```shell
git reset HEAD^
```

Con esto listo ya se pueden hacer las modificaciones que se quisieran y en los commits adecuados, cabe destacar que como estamos en medio del rebase no aparecerá en ninguna branch.

Y por últimos, ya después de todos los cambios hechos, para volver a la normalidad y terminar el rebase es necesario el siguiente comando

```shell
git rebase --continue
```

<!-- https://www.atlassian.com/git/tutorials/merging-vs-rebasing -->

## Trabajo en GitHub

### Fork

### Clone 

### Colaboración

### Pull Request

### Issues

<!-- https://guides.github.com/features/issues/ -->

### Milestones

### Wiki

### Proyectos

### Organización

### Gráficas





<!-- Referencias de imagenes -->

[gitcommit]: img/gitadd-gitcommit.png
[git-data]: img/git-data.png
[git-branch]: img/gitbranch.png
[git-branch-create]: img/gitbranch-create.png
[git-distribuido]: img/git-distribuido.png

## Referencias

- [What's the difference between HEAD, working tree and index, in Git - StackOverflow](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
- [Una referencia visual de Git - marklodato.github.io](https://marklodato.github.io/visual-git-guide/index-es.html)

## Anexos

### Manejo de linea de comandos de git

- Limpiar la consola ```clear```
- Moverse entre carpetas ```cd <direccion>``` o ```cd ..```
- listar todos los archivos incluso los ocultos ```ls -al```

### Manejo de archivos con VIM

- Para salir sin guardar cambios en los archivos es con ```:q```
- Para editar el archivo con ``a``
- Para salir y guardar cambios en los archivos es con ```:wq```

