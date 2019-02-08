# Curso Git|GitHub

## Introducción

### Acerca del control de versiones

Al momento de desarrollar es importante poder llevar un registro historico de todos los cambios generados por todos los involucrados en el proyecto, en eso radica la popularidad de los controladores de versiones de hoy en día. Nos permiten administrar cualquier desarrollo de software de una manera eficaz y rápida.

El correcto uso de esta tecnología puede ser un valioso aliado, ya que nos ahorra el hecho que tengamos que hacer nosotros mismos respaldos de archivos que a lo mejor nos olvidemos donde estén o modifiquemos en algun lugar que no sea el correcto, así como nos ofrece movernos libremente entre el historico de todos los archivos. También funciona perfecto para equipos de gran tamaña como también para quien trabaja en solitario por su flexibilidad en el flujo de trabajo.

### Git, una breve explicación

Git es un sistema de control de versiones distribuido, es decir, que existe el código fuente en el servidor y en los clientes donde se guarda el proyecto y hace una copia localmente en el equipo, siendo completamente independiente del servicio de alojamiento principal.

La gran ventaja que nos brinda es la seguridad de que si algun día llegará a corromperse algunos archivos en el servidor o alguien borrará el proyecto principal por accidente, cualquiera que tuviera una copia del programa antes de que pasará una de las situaciones anteriormente planteadas pudiesé ser el salvador del equipo pudiendo resubir el repositorio y seguiría el curso del desarrollo como si no hubiera pasado nada.  

![Control de versiones distribuido][git-distribuido]

> Git fue creado pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente, es decir Git nos proporciona las herramientas para desarrollar un trabajo en equipo de manera inteligente y rápida y por trabajo nos referimos a algún software o página que implique código el cual necesitemos hacerlo con un grupo de personas.  
> -Andrés en [Codigo Facilito](https://codigofacilito.com/articulos/que-es-git).

### Configuración

#### Inicial

Para usar git es necesario estar identificados con un usuario y correo para poder identificar de una manera rápida y sencilla quién esta haciendo los cambios en los repositorios.  

```git
git config --global user.name = <nombre>
git config --global user.email = <correo>
```

Para poder conocer las configuraciones de nuestro git se puede desplegar en un archivo en donde se almacena las configuraciones hechas.

```git
git config --global -e
```

#### Conexión con SSH

### Pedir ayuda a la linea de comandos

Es muy fácil perdernos entre tanto que aprender y por ello git nos puede proporcionar una guía bastante útil cuando la necesitemos respecto a los comandos que existen, por ello es importante conocer las diferentes maneras de pedir ayuda.

```git
git help
git help <comando>
git <comando> --help
```

<!-- Sin redactar-->

## ***Introducción***


### ¿Qué es un commit?
  >Sirve para almacenar los cambios de manera local donde se guarda el apuntador de los archivos preparados, unos metadatos con el autor y el mensaje explicativo de lo que sucedio en ese punto del tiempo  

![Breve ejemplo del proceso de un commit][gitcommit]

 >Se debe de escribir en tiempo presente y sea lo mas descriptivo posible

<!--![Explicación breve de como funciona un commit][git-data]--> 
  
#### ¿Qué es el Stage?
  > Es una especie de área de exhibición en git, donde se colocan los contenidos que se deben confirmar en el commit.

#### ¿Qué es status?
  >Muestra todas las rutas que tienen diferencias entre el archivo _index_ y la posición actual de _HEAD_, las rutas que tienen diferencias entre la rama que se esta trabajando y el archivo _index_ y las rutas de la rama en la que se esta trabjando que no están siendo seguidas por Git y que no estan siendo ignoradas por el archivo **.gitignore**.  [Documentación oficial de Git](https://git-scm.com/docs/git-status)  
  >Esto quiere decir que se visualizará el estado de todos los archivos que contengan cambios que no hayan sigo archivados con un commit en el espacio de trabajo.

  >Si esta en rojo quiere decir que es un nuevo archivo, si esta en amarillo quiere decir que se esta modificando y si esta en verde es el archivo que esta en el stage

#### ¿Qué es el HEAD?
  >Es el apuntador que se encuentra siempre en el ultimo commit realizado

#### ¿Qué es Index?
  >Es donde se coloca los archivos que desea que se confirmen en el repositorio  
  

### ¿Qué es una branch?
 > Una rama de git es simplemente un apuntador móvil apuntado a uno de los diferentes commits. La rama por defecto es la master. En cada commit que realicemos, la rama irá avanzando automaticamente.
 
![Apuntadores de la branch][git-branch]

 > Cuando se manejan distintas ramas se crea un nuevo apuntador para que se pueda mover libremente en ella, y se comportara de la misma manera como en la master, en donde _Head_ será el apuntador donde nos dira la rama con la que estemos trabajando

![Apuntador Head en la separación de la branch][git-branch-create]

## ¿Qué es un log?
> Muestra el historial de los commits


<!--Checar como personalizar los logs https://coderwall.com/p/euwpig/a-better-git-log-->




## Configuración inicial del proyecto

Para poder inicializar cualquier proyecto con un control de versiones es necesario tener una carptea de **.git**, está es el encargada de llevar todo el control de nuestros archivos y el espacio tiempo en el que se hicieron los cambios.
```
git init
```

## Comandos necesarios de aprender

Para poder agregar todos los cambios al escenario el siguiente comando lo hara
```
git add <archivo>
```
```
git add .
```

Para poder salvar todos los cambios en una linea de tiempo es necesario hacer un commit, identificandolo con un comando
```
git commit -m <mensaje>
```


## Comando de consola utiles

Para poder identificar si hubo algun cambio, se agrago nuevos archivos o carpetas el siguiente comando nos permite identificarlo de una manera grafico lo anterior dicho, ademas identificando si esta en el escenario o no
```
git status
```



El siguiente comando sirve para revertir los cambios y regresar los archivos en el ultimo commit  
```
git checkout -- .
```

## Manejo de linea de comandos de git

- Limpiar la consola ```clear```
- Moverse entre carpetas ```cd <direccion>``` o ```cd ..```
- listar todos los archivos incluso los oultos ```ls -al```

## Manejo de archivos con VIM
- Para salir sin guardar cambios en los archivos es con ```:q```



<!-- Referencias de imagenes -->

[gitcommit]: /img/gitadd-gitcommit.png
[git-data]: /img/git-data.png
[git-branch]: /img/gitbranch.png
[git-branch-create]: /img/gitbranch-create.png
[git-distribuido]: /img/git-distribuido.png

## ***Referencias***
- [What's the difference between HEAD, working tree and index, in Git - StackOverflow](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
- [Una referencia visual de Git - marklodato.github.io](https://marklodato.github.io/visual-git-guide/index-es.html)
