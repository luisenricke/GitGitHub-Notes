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

#### Inicial

Para usar git es necesario estar identificados con un usuario y correo para poder identificar de una manera rápida y sencilla quién esta haciendo los cambios en los repositorios.  

```git
git config --global user.name = <nombre>
git config --global user.email = <correo>
```

#### Conexión con SSH

#### Alias

Los alias sirven para acortar ciertos comandos que son dificiles de recordar y cansados de teclear, por ello es necesario declararlos de manera global para que en cualquier momento se pueda utilizar.

```git
git config --global alias.<alias> "<comando>"
git config --global alias.lg "log --oneline --decorate --all --graph"
git config --global alias.s "status -s -b"
```

<!--https://styde.net/crear-alias-de-comandos-con-git/-->

#### Archivo de configuración

Para poder consultar todas las configuraciones que se han efectuado hasta ahora es necesario ejecutar el siguiente comentario.

```git
git config --global -l
```

Para poder modificar directamente las configuraciones en el archivo es necesario ejecutar el siguiente comando.

```git
git config --global -e
```

### Pedir ayuda

Es muy fácil perdernos entre tanto que aprender y por ello git nos puede proporcionar una guía bastante útil cuando la necesitemos respecto a los comandos que existen, por ello es importante conocer las diferentes maneras de pedir ayuda.

```git
git help
git help <comando>
git <comando> --help
```

## ***Configuración inicial***

Para poder inicializar cualquier proyecto con un control de versiones es necesario tener una carptea de **.git**, está es el encargada de llevar todo el control de nuestros archivos y el espacio tiempo en el que se hicieron los cambios.

### Inicializando un repositorio

Si se esta iniciando desde cero el proyecto es necesario ejecutar el siguiente comando para que empiece a llevar el control de los archivos.

```git
git init
```

Se recomienda que despues de hacer lo anterior se agregue un archivo _README_ y se haga el primer commit porque es el archivo que sirve como una breve descripción del repositorio, una carta de presentación o simplemente información necesaria para entender lo que se desarrolla.

```git
git add README.md
git commit -m 'Initial commit'
```

### Clonando un repositorio

Si deseas modificar o contribuir a un repositorio ya existente es necesario descargarlo en tu computadora, con esto tendras una copia identica a la del servidor y así tener la posibilidad modificar todos los archivos como gustes.

```git
git clone [url]
git clone [url] <nombre>
```

Git permite clonar proyectos de dos maneras diferentes. La primera es através del protocolo HTTTPS pero también se puede usar el protocolo SSH. Cabe aclarar que la segunda opción tiene un filtro de seguridad para que identifique al usuario sin exponer datos confidenciales del desarrollador.

## ***Operaciones básicas con los comandos de Git***

### Ignorar archivos



### Revisar los cambios en el proyecto

Para poder identificar si hubo algun tipo de cambio, se agrago nuevos archivos o carpetas, es necesario utilizar **status**, que nos permite identificarlo de una manera grafica lo anterior dicho, ademas identificando si esta en el _stage_.

```git
git status
```

Una forma de abreviar la salida del comando y sea más visible lo que esta pasando en el stage, es poniendole la bandera de **short**.

```git
git status -s
```

Para poder conocer en el comando con que rama se está trabajando también pero de la forma acortada es agregandole la bandera de **branch**.

```git
git status -s -b
```

### Agregar archivos al Stage

Lo más adecuado a la hora de estar trabajando en un proyecto real es simplificar las tareas para que el desarrollo sea más agil y alcanzable y esto se tiene que ver reflejado en el nombramiento de los commits.

Hay varias maneras con las cuales se puede filtrar que archivos o carpetas se desea agregar al stage, esto ocacionara que en la busqueda de errores a través del tiempo sea más rápida y visible.

Para agregar un único archivo:

```git
git add <nombre del archivo>
git add ejemplo.html
```

Para agregar muchos archivos a la vez:

```git
git add <lista de archivos>
git add ejemplo.html css/style.css js/app.js
```

Para agregar una carpeta en especifico con todo su contenido:

```git
git add <nombre de la carpeta>/
git add js/
```

Para agregar todos los archivos con un tipo de extensión en la direccion actual:

```git
git add *.<nombre del tipo de archivo>
git add *.jpg
```

Para agregar todos los archivos con un tipo de extensión en todo el proyecto:

```git
git add "*.<nombre del tipo de archivo>"
git add "*.jpg"
```

Para agregar todos los archivos con un tipo de extensión en la carpeta especificada:

```git
git add <nombre de carpeta>/*.<nombre del tipo de archivo>
git add img/*.jpg
```

Para agregar todos excluyendo ciertos archivos o carpetas con filtro:

```git
git add .
git reset <filtro>
git reset  js/ css/ favicon.ico
```

### Haciendo una captura del tiempo

Para poder guardar todos los cambios que se generaron en los archivos que estaban en el stage, es necesario validarlo con un **commit**. Esto permitirá que se genere un registro de ese punto en el tiempo.

Se guardará el apuntador de los archivos que estaban en el _stage_, unos metadatos con el autor y el mensaje explicativo de lo que sucedio en ese punto del tiempo.

```git
git commit -m <mensaje>
git commit -m "Primer commit"
```

Existe una bandera para **commit** que hace que todos los archivos que hayan sido rastreados por el repositorio y hayan sufrido cambios sean agregados directamente al stage y se guarde a un apuntador del tiempo.

```git
git commit -am <mensaje>
git commit -am "Se actualizo index.html y los estilos"
```

### Checar diferencias entre el último **commit** y lo modificado

### Modificar el nombre de los archivos

### Eliminar archivos

### Checar el historial de las capturas

Sirve para mostrar el historial de los commits hechos localmente.

```git
git log
```

Para tener una mejor presentación de los datos en donde se despliega en una sola linea con el hash, el nombre del commit y en donde se encuentra el _Head_ es necesario agregarle una bandera al comando.

```git
git log --oneline
```

Para poder visualizar todos los cambios que se fueron generando de una manera gráfica es necesario agregarle dos banderas al comando para que se pueda mover entre branches y merges.

```git
git log --graph --decorate
```

Cabe destacar que las banderas del log antes mencionados se pueden combinar para checar de una mejor manera lo que esta pasando al proyecto, es desición de cada uno elegir cual es la más funcional para cada uno.

<!-- Referencias de imagenes -->
[gitcommit]: /img/gitadd-gitcommit.png
[git-data]: /img/git-data.png
[git-branch]: /img/gitbranch.png
[git-branch-create]: /img/gitbranch-create.png
[git-distribuido]: /img/git-distribuido.png

## ***Referencias***

- [What's the difference between HEAD, working tree and index, in Git - StackOverflow](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
- [Una referencia visual de Git - marklodato.github.io](https://marklodato.github.io/visual-git-guide/index-es.html)


<!--Sin editar del curso-->

## Anexos

## ***Conceptos de Git***

### Staging area / Index

Es una especie de área de almacenamiento en donde se colocan los contenidos que se deben confirmar en el commit.

### Head

Es el apuntador que se encuentra siempre en el último commit realizado.

### Status

> _Muestra todas las rutas que tienen diferencias entre el archivo **index** y la posición actual de **HEAD**, las rutas que tienen diferencias entre la rama que se esta trabajando y el archivo **index** y las rutas de la rama en la que se esta trabjando que no están siendo seguidas por Git y que no estan siendo ignoradas por el archivo **.gitignore**._ [Documentación oficial de Git](https://git-scm.com/docs/git-status)  

Esto quiere decir que se visualizará el estado de todos los archivos que contengan cambios que no hayan sigo archivados con un commit en el espacio de trabajo.

### Branch

Una rama de git es simplemente un apuntador ubicado en uno de los diferentes commits. La rama por defecto es la master. En cada commit que realicemos, la rama irá avanzando automaticamente.

<!--![Apuntadores de la branch][git-branch]-->

Cuando se manejan distintas ramas se crea un nuevo apuntador para que se pueda mover libremente en ella, y se comportara de la misma manera como en la master, en donde _Head_ será el apuntador donde nos dira la rama con la que estemos trabajando.

<!--![Apuntador Head en la separación de la branch][git-branch-create]-->

### Comando de consola utiles

El siguiente comando sirve para revertir los cambios y regresar los archivos en el ultimo commit.

```git
git checkout -- .
```

### Manejo de linea de comandos de git

- Limpiar la consola ```clear```
- Moverse entre carpetas ```cd <direccion>``` o ```cd ..```
- listar todos los archivos incluso los oultos ```ls -al```

### Manejo de archivos con VIM

- Para salir sin guardar cambios en los archivos es con ```:q```