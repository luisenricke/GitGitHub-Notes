# Guía de commits

Es necesario establecer algunas reglas para la interacción entre los desarrolladores respecto a los mensajes de commit.

Cada mensaje de los commits consta de un encabezado, un cuerpo y un pie de página. El encabezado tiene un formato especial que incluye un tipo, un alcance y un tema:

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

El encabezado es obligatorio y el alcance del encabezado es opcional.

Cualquier línea del mensaje de confirmación no puede tener más de 100 caracteres! Esto permite que el mensaje sea más fácil de leer en GitHub así como en varias herramientas de git.

El pie de página debe contener una referencia de cierre a una cuestión, si la hubiera.

Si el commit se revierte a una versión anterior, debería empezar por ``revert:`` seguido del encabezado de la confirmación revertida. En el cuerpo debería decir: ``This reverts commit <hash>``, donde el hash es el SHA del commit que se está revirtiendo.

* **build**: Cambios que afectan al sistema de construcción o dependencias externas (ejemplos: gulp, broccoli, npm)
* **docs**: Cambios sólo en la documentación
* **feat**: Una nueva funcionalidad
* **fix**: Una corrección de errores
* **perf**: Un cambio de código que mejora el rendimiento
* **refactor**: Un cambio de código que no corrige un error ni añade una característica
* **style**:  Cambios que no afectan el significado del código (espacio en blanco, formato, falta de puntos y coma, etc.)
* **test**: Añadir pruebas que faltan o corregir pruebas existentes



## Referencias

- [Angular CONTRIBUTING](https://github.com/angular/angular/blob/master/CONTRIBUTING.md)
- [DEV Community 👨‍💻👩‍💻 | Enhance your git log with conventional commits](https://dev.to/maxpou/enhance-your-git-log-with-conventional-commits-3ea4)

