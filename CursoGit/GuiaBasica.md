# Curso Git | GitHub

## ***Introducción***

### Acerca del control de versiones

Al momento de desarrollar es importante poder llevar un registro historico de todos los cambios generados por todos los involucrados en el proyecto, en eso radica la popularidad de los controladores de versiones de hoy en día. Nos permiten administrar cualquier desarrollo de software de una manera eficaz y rápida.

El correcto uso de esta tecnología puede ser un valioso aliado, ya que nos ahorra el hecho que tengamos que hacer nosotros mismos respaldos de archivos que a lo mejor nos olvidemos donde estén o modifiquemos en algun lugar que no sea el correcto, así como nos ofrece movernos libremente entre el historico de todos los archivos. También funciona perfecto para equipos de gran tamaña como también para quien trabaja en solitario por su flexibilidad en el flujo de trabajo.

### Git, una breve explicación

> _Git fue creado pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente, es decir Git nos proporciona las herramientas para desarrollar un trabajo en equipo de manera inteligente y rápida y por trabajo nos referimos a algún software o página que implique código el cual necesitemos hacerlo con un grupo de personas._
> -Andrés en [Codigo Facilito](https://codigofacilito.com/articulos/que-es-git).

Git es un sistema de control de versiones distribuido, es decir, que existe el código fuente en el servidor y en los equipos donde se guarda el proyecto, siendo completamente independiente del servicio de alojamiento principal.

La gran ventaja que nos brinda es la seguridad de que si algun día llegará a corromperse algunos archivos en el servidor o alguien borrará el proyecto principal por accidente, cualquiera que tuviera una copia del programa antes de que pasará una de las situaciones anteriormente planteadas pudiesé ser el salvador del equipo pudiendo resubir el repositorio y seguiría el curso del desarrollo como si no hubiera pasado nada.  

<!--![Control de versiones distribuido][git-distribuido]-->

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

Configuración para Windows:

```shell
git config --global core.autocrlf true
```

Configuración para OSX y Linux:

```shell
git config --global core.autocrlf input
```

Si no se configura esto, puede arrojar la siguiente advertencia ``warning: LF will be replaced by CRLF in [FILE_NAME]. The file will have its original line endings in your working directory.``, en donde se dispara cuando se están haciendo los commits.

#### Conexión con SSH

## ***Obteniendo un repositorio Git***

Para poder manejar cualquier proyecto con git es necesario tener una carpeta de **.git**, está es el encargada de llevar todo el control de nuestros archivos y el espacio tiempo en el que se hicieron los cambios.

### Inicializando un repositorio

Si el proyecto no ha tenido ninguna intervención con git es necesario inicializarlo para que empiece a llevar el control de todos los archivos.

```shell
git init
```

Se recomienda que después inicializar el proyecto se agregue un archivo llamado _README.md_ y se haga el primer commit, ya que este archivo en GitHub o GitLab se muestra en la página principal del proyecto y sirve para mostrar una breve descripción del repositorio o una carta de presentación o simplemente información necesaria para entender lo que se desarrolló.

```shell
git add README.md
git commit -m "Initial commit"
```

### Clonando un repositorio

Si deseas modificar o contribuir a un repositorio ya existente es necesario descargarlo en tu computadora, con esto tendrás una copia idéntica a la del servidor y así tienes la posibilidad de modificar todos los archivos como gustes.

```shell
git clone <url>
git clone <url> <nombre-del-proyecto>
```

Git permite clonar proyectos de dos maneras diferentes. La primera es através del protocolo HTTTPS pero también se puede usar el protocolo SSH. Cabe aclarar que la segunda opción tiene un filtro de seguridad para que identifique al usuario sin exponer datos confidenciales del desarrollador.

## ***Operaciones básicas con los comandos de Git***

### Ignorar archivos

El archivo ``.gitignore`` especifica todos los archivos que no se podrán rastrear por git. Los archivos que ya hayan sido reastreados no sufriran los cambios. En cada linea de este archivo se especifica un patrón. Cuando Git decide que ignorar, normalmente checa todos los patronoes alojados en estos archivos.

```shell
touch .gitignore
```

Para ahorrar un poco de tiempo se puede recurrir a la pagina web de [gitignore.io](https://www.gitignore.io/). Esta web nos ayuda a configurar de una manera fácil y rapida dependiendo del proyecto el archivo.

### Revisar los cambios en el proyecto

Para poder identificar si hubo algun tipo de cambio, se agrago nuevos archivos o carpetas, es necesario utilizar **status**, que nos permite identificarlo de una manera grafica lo anterior dicho, ademas identificando si esta en el _stage_.

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

### Agregar archivos al Stage

Lo más adecuado a la hora de estar trabajando en un proyecto real es simplificar las tareas para que el desarrollo sea más agil y alcanzable y esto se tiene que ver reflejado en el nombramiento de los commits.

Hay varias maneras con las cuales se puede filtrar que archivos o carpetas se desea agregar al stage, esto ocacionara que en la busqueda de errores a través del tiempo sea más rápida y visible.

Para agregar un único archivo:

```shell
git add <nombre del archivo>
git add ejemplo.html
```

Para agregar muchos archivos a la vez:

```shell
git add <lista de archivos>
git add ejemplo.html css/style.css js/app.js
```

Para agregar una carpeta en especifico con todo su contenido:

```shell
git add <nombre de la carpeta>/
git add js/
```

Para agregar todos los archivos con un tipo de extensión en la direccion actual:

```shell
git add *.<nombre del tipo de archivo>
git add *.jpg
```

Para agregar todos los archivos con un tipo de extensión en todo el proyecto:

```shell
git add "*.<nombre del tipo de archivo>"
git add "*.jpg"
```

Para agregar todos los archivos con un tipo de extensión en la carpeta especificada:

```shell
git add <nombre de carpeta>/*.<nombre del tipo de archivo>
git add img/*.jpg
```

Para agregar todos excluyendo ciertos archivos o carpetas con filtro:

```shell
git add .
git reset <filtro>
git reset  js/ css/ favicon.ico
```

### Haciendo una captura del tiempo

Para poder guardar todos los cambios que se generaron en los archivos que estaban en el stage, es necesario validarlo con un **commit**. Esto permitirá que se genere un registro de ese punto en el tiempo.

Se guardará el apuntador de los archivos que estaban en el _stage_, unos metadatos con el autor y el mensaje explicativo de lo que sucedio en ese punto del tiempo.

```shell
git commit -m <mensaje>
git commit -m "Primer commit"
```

Existe una bandera para **commit** que hace que todos los archivos que hayan sido rastreados por el repositorio y hayan sufrido cambios sean agregados directamente al stage y se guarde a un apuntador del tiempo.

```shell
git commit -am <mensaje>
git commit -am "Se actualizo index.html y los estilos"
```

### Checar diferencias entre el último **commit** y lo modificado

Al identificar los cambios, se puede llegar a saber en que se estaba trabajando la ultima vez que se modificaron los cambios

```shell
git diff
```

Con el anterior comando es imposible conocer los cambios entre HEAD y lo que hay en el stage, por ello hay una bandera especial que se encarga de eso.

```shell
git diff --staged
```

### Eliminar archivos del stage y los cambios hechos, modificar el nombre de los commits

Para poder modificar el nombre del ultimo commit generado es necesario utilizar

```java
git commit --amend
```

Para poder eliminar un archivo del stage es necesario ocupar un comando especial

```shell
git reset HEAD <nombre del archivo>
```

Para poder traer de vuelta al stage todos los cambios de la ultima captura es necesario ocupar un reset con una bandera especial del commit que se quiera actualizar, en este caso cuando se ocupa el HEAD^ para traer el ultimo commit que esta antes del HEAD, y con ello se puede hacer de nuevo el commit con un nuevo nombre

```shell
git reset --soft HEAD^
```

Para poder dejar un archivo como estaba en el ultimo commit es necesario ejecutar un comando que pudiera ser muy delicado si hay cambios importantes que no se encuentren en el stage.

```shell
git checkout -- <nombre del archivo>
```

El siguiente comando sirve para revertir los cambios y regresar los archivos al ultimo commit de todos los cambios que se realizaron y que no se encuentren en el stage.

```shell
git checkout -- .
```

### Viajar en el tiempo 

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

### Cambiar y eliminar archivos con git

```shell
git mv <nombre actual> <nombre nuevo>
```

```shell
git rm <nombre>
```

### Checar el historial de las capturas

Sirve para mostrar el historial de los commits hechos localmente.

```shell
git log
```

Para tener una mejor presentación de los datos en donde se despliega en una sola linea con el hash, el nombre del commit y en donde se encuentra el _Head_ es necesario agregarle una bandera al comando.

```shell
git log --oneline
```

Para poder visualizar todos los cambios que se fueron generando de una manera gráfica es necesario agregarle dos banderas al comando para que se pueda mover entre branches y merges.

```shell
git log --graph --decorate
```

Cabe destacar que las banderas del log antes mencionados se pueden combinar para checar de una mejor manera lo que esta pasando al proyecto, es desición de cada uno elegir cual es la más funcional para cada uno.

### Manejo de branchs

Para checar todas las ramas existentes y en cual se está

```shell
git brach
```

Para moverse entre ramas

```shell
git checkout <nombre-rama>
```

Para poder crear nuevas ramas es necesario ocupar el comando

```shell
git brach <nombre-branch>
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

Para poder hacer cualquier merge es necesario estar en la rama en la cual se quieran agregar todos los cambios.

#### Merge: Fast-fordward

Para unir las ramas

```shell
git merge <rama a unir>
```

#### Merge: Automatico

```shell
git merge <rama a unir>
```

#### Merge: Con conflictos

Primero se debe de hacer el merge y despues el commit de la resolución del conflicto

### Tags
<!--Investigar que es un tag-->

Para ver todos los tags

```shell
git tag 
```

Para crear un tag es necesario

```shell
git tag <nombre del tag>
git tag -a <version> -m <mensaje>
git tag -a <version> <hash del commit al que se quiera poner tag> -m <mensaje>
```

Para borrar un tag es necesario

```shell
git tag -d <nombre del tag>
```

Para ver todos los cambios hechos en ese punto de la historia con el tag

```shell
git show <nombre del tag>
```

<!-- Referencias de imagenes -->
[gitcommit]: img/gitadd-gitcommit.png
[git-data]: img/git-data.png
[git-branch]: img/gitbranch.png
[git-branch-create]: img/gitbranch-create.png
[git-distribuido]: img/git-distribuido.png

## ***Referencias***

- [What's the difference between HEAD, working tree and index, in Git - StackOverflow](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
- [Una referencia visual de Git - marklodato.github.io](https://marklodato.github.io/visual-git-guide/index-es.html)

<!--Sin editar del curso-->

## Anexos

### Pedir ayuda

Es muy fácil perdernos entre tanto que aprender y por ello git nos puede proporcionar una guía bastante útil cuando la necesitemos respecto a los comandos que existen, por ello es importante conocer las diferentes maneras de pedir ayuda.

```shell
git help
git help <comando>
git <comando> --help
```

### Manipular el archivo de configuración

Muchas de las veces es necesario consultar nuestras configuraciones globales para identificar que variables esta tomando nuestro control de versiones.

```shell
git config --global -l
```

De igual manera, aveces, se tendrá la necesidad de modificar las configuraciones de una manera sencilla y rápida.

```shell
git config --global -e
```



## ***Conceptos de Git***

### Staging area / Index

Es una especie de área de almacenamiento en donde se colocan los contenidos que se deben confirmar en el commit.

### Head

Es el apuntador que se encuentra siempre en el último commit realizado.

### Status

> _Muestra todas las rutas que tienen diferencias entre el archivo **index** y la posición actual de **HEAD**, las rutas que tienen diferencias entre la rama que se esta trabajando y el archivo **index** y las rutas de la rama en la que se esta trabjando que no están siendo seguidas por Git y que no estan siendo ignoradas por el archivo **.gitignore**._ [Documentación oficial de Git](https://git-scm.com/docs/git-status)  

Esto quiere decir que se visualizará el estado de todos los archivos que contengan cambios que no hayan sigo archivados con un commit en el espacio de trabajo.

### Branch

Una rama de git es simplemente un apuntador ubicado en uno de los diferentes commits. La rama por defecto es la master. En cada commit que realicemos, la rama irá avanzando automaticamente. Por default, la rama que se utiliza es la master.

<!--![Apuntadores de la branch][git-branch]-->

Cuando se manejan distintas ramas se crea un nuevo apuntador para que se pueda mover libremente en ella, y se comportara de la misma manera como en la master, en donde _Head_ será el apuntador donde nos dira la rama con la que estemos trabajando.

<!--![Apuntador Head en la separación de la branch][git-branch-create]-->

### Merge

<!--investigar-->

#### Fast-forward

#### Uniones automaticas

#### Manual (Merge commit)

### Manejo de linea de comandos de git

- Limpiar la consola ```clear```
- Moverse entre carpetas ```cd <direccion>``` o ```cd ..```
- listar todos los archivos incluso los oultos ```ls -al```

### Manejo de archivos con VIM

- Para salir sin guardar cambios en los archivos es con ```:q```
- Para editar el archivo con ``a``
- Para salir y guardar cambios en los archivos es con ```:wq```

