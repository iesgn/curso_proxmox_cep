# ACTIVIDAD Nº 2

## TÍTULO DE LA ACTIVIDAD: Creación de una máquina virtual Windows

## TEXTO DE LA ACTIVIDAD

En esta actividad vamos a crear una máquina virtual con el sistema operativo Windows. Para ello:

1. Sube una imagen ISO de Windows 10. (**Nota: Si utilizas VirtualBox como sistema de virtualización de Proxmox, tal vez un Windows 10 sea muy lento. Puedes utilizar una versión más antigua como un windows 7, o un Windows Server que puede ser más liviano**).
)
2. Sube la imagen ISO de los drivers VirtIO.
3. Crea una nueva máquina virtual en Proxmox, con la configuración que hemos indicado en el contenido del módulo (no olvides coger el tipo de disco duro y la interfaz de red como VirtIO).
4. Añade a la máquina un CDROM con los drivers VirtIO y configura la máquina para que arranque de forma adecuada con el instalador de Windows.
5. Instala de forma adecuada los drivers VirtIO para detectar el disco duro durante la instalación y terminar la instalación de la máquina.
6. Una vez instalada la máquina accede a ella desde un terminal de Proxmox VE.
7. Configura de forma adecuada los drivers de la tarjeta de red para que tenga la máquina tenga acceso a internet.

Para superar la actividad deberás entregar en un fichero comprimido los siguientes pantallazos:

1. Un pantallazo donde se vea el apartado **Hardware** de la máquina que has creado.
2. Un pantallazo donde se vea el apartado **Options** de la máquina para comprobar el orden de arranque configurado.
3. Un pantallazo donde se vea el acceso a la máquina virtual una vez instalada usando la consola de Proxmox VE.
4. Un pantallazo donde se compruebe que la máquina tiene acceso a internet.


## RECURSOS

* Conexión a Internet

## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

Sí

## ¿ES UNA ACTIVIDAD INDIVIDUAL O DE GRUPO?

Individual

## ¿ES UNA ACTIVIDAD CALIFICABLE?

Sí

### ¿Tiene que ser calificada por el tutor/a? (S/N)

Sí

### ¿Es de calificación automática?

No

### ¿Es calificada por el resto de compañeros/as del curso? (S/N)

No

## EVALUACIÓN

* Se entregan los documentos, contienen lo solicitado y los contenidos son originales.

## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

No

## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

1 hora