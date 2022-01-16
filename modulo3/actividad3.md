# ACTIVIDAD Nº 3

## TÍTULO DE LA ACTIVIDAD: Creación de un escenario de trabajo (1ª parte)

## TEXTO DE LA ACTIVIDAD

Durante la realización de las tareas voluntarias de este curso os vamos a guiar para montar un escenario de prácticas que podríamos usar con nuestros alumnos. Por lo tanto vamos a crear una infraestructura en Proxmox VE y vamos a configurarla de manera adecuada según los requisitos que se presentarán posteriormente.

Tienes que tener en cuenta los siguientes aspectos:

1. El escenario que vamos a montar lo vamos a hacer secuencialmente en las distintas tareas voluntarias que tenemos en el curso.
2. En estas tareas no vamos a ampliar conocimientos extras que no se hayan estudiado y trabajado en las tareas obligatorias.
3. En estas tareas nos vamos a centrar más en la configuración de las máquinas que creemos en nuestro escenario. por lo tanto los conocimientos que puedes adquirir en su realización no se corresponden exactamente con los aprendidos en este curso de Poxmox.

El escenario que vamos a montar nos permitirá montar una sería de máquinas y contenedores que le den servicio a máquinas virtuales o contenedores que estén en un red interna. Los servicios que vamos a ofrecer son enrutamiento, NAt, DHCP y DNS. De tal manera que el objetivo que vamos a conseguir es que máquinas/contenedores que estén conectada a una red interna tengan conexión al anterior y que su direccionamiento se configure de forma automática.

![escenario](img/escenario_tareas_voluntarias.drawio.png)

* Crearemos una red interna donde crearemos dos máquinas virtuales y un contenedor.
* La máquina virtual **router** estará conectada a la red externa y a la interna y ofrecerá el servicio de enrutamiento y de NAT. Será la puerta de enlace de las máquinas de la red local y permitira el acceso al exterior a estas máquinas.
* La máquina virtual **cliente**, será la máquina que utilicemos en la red interna para probar si funcionan los servicios que vamos a ofrecer.
* El contenedor **servicios** estará conectado también a la red interna y ofrecerá el servicio y DHCP y DNS a la máquina **cliente**.



Para superar la actividad deberás entregar en un fichero comprimido los siguientes pantallazos:


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