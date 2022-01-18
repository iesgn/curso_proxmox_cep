# ACTIVIDAD Nº 3

## TÍTULO DE LA ACTIVIDAD: Creación de un escenario de trabajo (1ª parte)

## TEXTO DE LA ACTIVIDAD

Durante la realización de las tareas voluntarias de este curso os vamos a guiar para montar un escenario de prácticas que podríamos usar con nuestros alumnos. Por lo tanto vamos a crear una infraestructura en Proxmox VE y vamos a configurarla de manera adecuada según los requisitos que se presentarán posteriormente.

Tienes que tener en cuenta los siguientes aspectos:

1. El escenario que vamos a montar lo vamos a hacer secuencialmente en las distintas tareas voluntarias que tenemos en el curso.
2. En estas tareas no vamos a ampliar conocimientos extras que no se hayan estudiado y trabajado en las tareas obligatorias.
3. En estas tareas nos vamos a centrar más en la configuración de las máquinas que creemos en nuestro escenario, por lo tanto los conocimientos que puedes adquirir en su realización no se corresponden exactamente con los aprendidos en este curso de Proxmox.

El escenario que vamos a montar nos permitirá montar una sería de máquinas y contenedores que le den servicio a máquinas virtuales o contenedores que estén conectados a una red interna. Los servicios que vamos a ofrecer son enrutamiento, NAT, DHCP y DNS. De tal manera que el objetivo que vamos a conseguir es que máquinas/contenedores que estén conectadas a una red interna tengan conexión al exterior y que su direccionamiento se configure de forma automática.

![escenario](img/escenario_tareas_voluntarias.drawio.png)

* Crearemos una red interna donde crearemos dos máquinas virtuales y un contenedor.
* La máquina virtual **router** estará conectada a la red externa y a la interna y ofrecerá el servicio de enrutamiento y de NAT. Será la puerta de enlace de las máquinas de la red local y permitirá el acceso al exterior a estas máquinas.
* La máquina virtual **cliente**, será la máquina que utilicemos en la red interna para probar si funcionan los servicios que vamos a ofrecer.
* El contenedor **servicios** estará conectado también a la red interna y ofrecerá el servicio y DHCP y DNS a la máquina **cliente**.

En esta primera tarea simplemente vamos a crear una nueva máquina virtual con el el sistema operativo Debian 11 Bullseye. Para ello realiza los siguientes pasos:

1. Sube la imagen ISO de GNU/Linux Debian 11 que puedes descargar en este [enlace](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-11.2.0-amd64-netinst.iso).
2. Crea e instala una máquina virtual con el sistema GNU/Linux Debian 11. No tiene que tener entorno gráfico, por lo tanto los recursos podrían ser 512 Mb de RAM y 5 Gb de disco duro. La máquina se debe llamar **debian-base**.
3. Una vez instalada la máquina accede a ella desde un terminal de Proxmox VE.

Para superar la actividad deberás entregar en un fichero comprimido los siguientes pantallazos:

1. Un pantallazo donde se vea el apartado **Hardware** de la máquina que has creado.
2. Un pantallazo donde se vea el acceso a la máquina virtual una vez instalada.

## RECURSOS

* Conexión a Internet

## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

No

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