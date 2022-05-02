# Ejemplo 2: Aislamiento de usuarios

En el ejemplo anterior todos los usuarios trabajaban sobre los mismos recursos. En algunos escenarios sería deseable que cada usuario pudiera gestionar sus recursos. Esta idea vendría muy bien en la utilización de Proxmox VE en un centro educativo: cada alumno podría gestionar sus recursos y no podría interferir en los recursos de un compañero. 

Para conseguir este comportamiento vamos a asignar a cada usuario un Grupo de recursos y le vamos a dar los permisos necesarios para que el usuario sólo pueda gestionar los recursos que pertenecen a su grupo de recursos.

Además podríamos tener un grupo de profesores que fueran administradores y que tuvieran acceso a todas las funcionalidades.

## Configuración del escenario

1. Vamos a crear un grupo **Profesores** al que le vamos a asignar el rol de *Administrator*.
2. Para cada usuario que creemos para un alumno crearemos un Grupo de recursos. Por ejemplo vamos a crear el usuario `alumno1` y el grupo de recursos `Proyecto_de_alumno1`.
3. A cada alumno le vamos a asignar los roles de `PVEDatastoreUser`, `PVEVMAdmin` y `PVEPoolUSer` para el grupo de recursos asociado. DE esta manera cada alumno podrá gestionar sus máquinas si están creados en su grupo de recursos.

Hemos creado el grupo **Profesores** con el usuario **profesor1**:

![usuarios](img/usuario18.png)

Además hemos creado dos usuarios alumnos (estos usuarios no lo hemos asignados a ningún grupo):

![usuarios](img/usuario19.png)

Hemos creado dos grupos de recursos para cada uno de los usuarios alumnos:

![usuarios](img/usuario20.png)

Para que los usuarios puedan crear máquinas virtuales en sus grupos de recursos necesitarán que los pool de almacenamientos que tenemos definidos sean miembros del grupo de recurso. Por loq ue para cada grupo de recursos le añadimos los pools de almacenamientos que queremos que usen los usuarios:

![usuarios](img/usuario21.png)

Y por último asignamos los permisos:

![usuarios](img/usuario22.png)

## Prueba de funcionamiento

1. Accedemos con el usuario `alumno1` y comprobamos que sólo vemos el grupo de recursos `Proyecto_de_alumno1`. Este usuario sólo tiene permiso para crear máquinas dentro de este grupo de recursos. Podemos probar a crear una máquina en su grupo de recurso:

![usuarios](img/usuario23.png)

2. Al acceder con el usuario `alumno2` no damos cuenta que sólo se ve su grupo de recursos `Proyecto_de_alumno2`. No puede ver, ni modificar, ni borrar las máquinas del `alumno1`. Este usuario puede crear una máquina en sus grupo de recursos:

![usuarios](img/usuario24.png)

3. Si accede el usuario `profesor1` podrá gestionar todas las máquinas de todos los usuarios:

![usuarios](img/usuario25.png)