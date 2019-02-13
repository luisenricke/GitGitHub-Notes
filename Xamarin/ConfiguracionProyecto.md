# Pasos para configurar un nuevo proyecto

1. Ir a ``File -> New -> Project``
2. Ir a ``Cross-Platform`` y escoger ``Xamarin.Forms``

    *Nota*: Para poder identificar de una mejor manera cada proyecto que se desarrolla en Xamarin, es adecuado seguir una nomeclatura para el nombre.
    ``NombreEmpresa.NombreProyecto.PlataformaDesarrollada``  
    Por ejemplo: **ITTG.SGK.App**

    *Nota*: Para no producir cualquier error con el proyecto es necesario localizarlo lo mas cercano a raiz, ya que se presenta un error con la longitud de los caracteres que puede aceptar *Xamarin Forms*. El error que puede salir es ``System.IO.PathTooLongException: The specified path, file name, or both are too long. The fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters.``

3. Escoger ``Black`` con ``Shared Project``, esto nos permite crear un nuevo proyecto completamente vacio con la capacidad de compartir archivos y funcionalidades con otros proyectos.
4. Es necesario descargar todas las librerías y paqueterias para correr el proyecto, por eso, debemos de ir explorador de archivos, darle click izquiero a la solución del projecto y escoger ``Rebuild Solution``.

    *Nota*: Cada que se hagan cambios importantes en las configuraciones del proyecto es necesario repetir este paso para poder evitar crear errores al proyecto.

    *Nota*: Es normal que en las primeros rebuils tarde demasiado pero conforme se mapee el proyecto se recompilara cada vez más rápido.

5. Es necesario crear un nuevo proyecto de tipo ``Shared Project``, nos vamos a la solución, damos click izquierdo, buscamos ``Add``, seleccionamos ``New Project``, en la barra de busqueda ponemos ``Shared project``, utilizaremos la misma nomeclatura para el proyecto pero ahora con la diferencia es que en vez de ``App`` se ocupará ``Core`` y seleccionamos la opción que ocupa Visual C#.
6. Creamos una nueva carpeta con el nombre ``Core`` y arrastamos los dos proyectos que no tiene que ver con Android, IOS ni UWP
7. Se agregan las referencias de los proyectos moviles al proyecto ``Core``, nos vamos a la raiz de cada proyecto movil, le damos click izquierdo, esocgemos ``Add``, seleccionamos ``Reference`` y seleccionamos el proyecto ``Core``.

    *Nota*: Para poder llevar a cabo este paso es necesario cerrar y volver el proyecto, por un bug que se desconoce hasta ahora.

8. Para poder usar librerías nos tenemos que ir a la raiz del proyecto, darle click izquierdo, seleccionar ``Manage Nugget Package Solution``, se busca la librería deseada y se descarga para los tres proyectos móviles. Las librerías que son requeridas para cada proyecto y que no son agregadas automaticamente son: ``MvvmLightLibs``, ``sqlite-net-pcl``, ``System.Net.Http`` y ``Newtonsoft.Json``.

    *Nota*: Es necesario tener actualizado todas las librerías para su correcto funcionamiento.

9. Crear el sistema de carpetas en el shared project de ``Core``, el cual se compone de las carpetas de ``BL``, ``Data``, ``Model`` que tiene dentro la carpeta ``Entities``, ``OS``, ``Service`` y ``ViewModel`` con sus respectivas clases e interfaces necesarias para funcionar.  
    - Agregar ``SQLiteDataContext.cs`` en Data
    - Agregar ``DependecyService.cs`` en OS
    - Agregar ``IDB.cs`` en OS
    - Agregar ``INavigationService.cs`` en OS
    - Agregar ``WebApiClient.cs`` en Service
10. Crear el sistema de carpetas en el shared project de ``App``, el cual se compone de las carpetas de ``OS`` y ``Views``.
    - Agregar ``NavigationService.cs`` en OS
11. Crear el sistema de carpetas en todos los proyectos moviles, el cual se compone de ``OS``
    - Agregar ``DB.cs`` en OS