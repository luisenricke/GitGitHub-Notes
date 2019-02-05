# Curso Git|GitHub

## ***Introducción***

### ¿Qué es git? 
  > Git fue creado pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente, es decir Git nos proporciona las herramientas para desarrollar un trabajo en equipo de manera inteligente y rápida y por trabajo nos referimos a algún software o página que implique código el cual necesitemos hacerlo con un grupo de personas.  
  > -Andrés en [Codigo Facilito](https://codigofacilito.com/articulos/que-es-git).

### ¿Qué es un commit?
  >Sirve para almacenar los cambios de manera local donde se guarda el apuntador de los archivos preparados, unos metadatos con el autor y el mensaje explicativo de lo que sucedio en ese punto del tiempo  

![Breve ejemplo del proceso de un commit][gitcommit]

<!--![Explicación breve de como funciona un commit][git-data]--> 
  
#### ¿Qué es el HEAD?
  >Es el apuntador que se encuentra siempre en el ultimo commit realizado

#### ¿Qué es Index?
  >Es donde se coloca los archivos que desea que se confirmen en el repositorio  
  

### ¿Qué es status?
  >Muestra todas las rutas que tienen diferencias entre el archivo _index_ y la posición actual de _HEAD_, las rutas que tienen diferencias entre la rama que se esta trabajando y el archivo _index_ y las rutas de la rama en la que se esta trabjando que no están siendo seguidas por Git y que no estan siendo ignoradas por el archivo **.gitignore**.  [Documentación oficial de Git](https://git-scm.com/docs/git-status)  
  >Esto quiere decir que se visualizará el estado de todos los archivos que contengan cambios que no hayan sigo archivados con un commit en el espacio de trabajo.

### ¿Qué es una branch?
 > Una rama de git es simplemente un apuntador móvil apuntado a uno de los diferentes commits. La rama por defecto es la master. En cada commit que realicemos, la rama irá avanzando automaticamente.
 
![Apuntadores de la branch][git-branch]

 > Cuando se manejan distintas ramas se crea un nuevo apuntador para que se pueda mover libremente en ella, y se comportara de la misma manera como en la master, en donde _Head_ será el apuntador donde nos dira la rama con la que estemos trabajando

![Apuntador Head en la separación de la branch][git-branch-create]


## Configuración inicial del enterno

Para usar git es necesario estar identificados con un usuario y correo para poder identificar de una manera rápida y sencilla quién esta haciendo los cambios en el repositorio.  
```
git config --global user.name = <nombre>
git config --global user.email = <correo>
```

Para poder conocer las configuraciones de nuestro git se puede desplegar en un archivo en donde se almacena las configuraciones hechas
```
git config --global -e
```

## Configuración inicial del proyecto

Para poder inicializar cualquier proyecto con un control de versiones es necesario tener una carptea de **.git**, está es el encargada de llevar todo el control de nuestros archivos y el espacio tiempo en el que se hicieron los cambios.
```
git init
```

## Comandos necesarios de aprender

Para poder agregar todos los cambios al escenario el siguiente comando lo hara
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


## ***Ayuda***  

Con el siguiente comando podemos pedir a git que nos de más información en general  
```
git help
```

Para poder pedir información de un comando en especifico, sería de la siguiente manera
```
git help <comando>
```

<!-- Referencias de imagenes -->

[gitcommit]: /img/gitadd-gitcommit.png
[git-data]: /img/git-data.png
[git-branch]: /img/gitbranch.png
[git-branch-create]: /img/gitbranch-create.png

## ***Referencias***
- [What's the difference between HEAD, working tree and index, in Git - StackOverflow](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)