# ACTIVIDAD Nº 1

## TÍTULO DE LA ACTIVIDAD: Creación de un red interna

## TEXTO DE LA ACTIVIDAD

En esta actividad vamos a configurar la red interna de nuestro escenario, para ello:

1. Crea un bridge que llamaremos `vmbr100`, configuralo con la ip `10.0.0.100/24`.
2. Crea una nueva máquina virtual (te sugiero que uses una sistema operativo Debian 11 para que sea más parecido a los contenidos mostrados en el curso) que se llamará `router` conectada al bridge principal `vmbr0` y al nuevo bridge que has creado. Esta máquina la puedes crear a partir de otra (con un clonado o usando una plantilla).
3. Configura la nueva interfaz de la máquina virtual de forma estática con la dirección `10.0.0.1/24`.
4. Crea un contenedor LXC, llamado `cliente`, conectado al nuevo bridge que has creado. En el proceso de creación configura su interfaz de forma estática con la ip `10.0.0.2/24` y gateway el equipo `router` es decir la `10.0.0.1`.
5. Ejecuta un ping desde la máquina virtual al contenedor para comprobar la conectividad.
6. En la siguiente actividad vamos a seguir trabajando con estas máquinas.

Para superar la actividad deberás entregar en un fichero comprimido los siguientes pantallazos:

1. Un pantallazo donde se vea el apartado **Hardware** de la máquina que has creado.
2. Un pantalalzo donde se vea la salida del comando `ip a` en la máquina virtual, para comprobar las direcciones IP de las interfaces.
3. Un pantallazo donde se vea el apartado **Networks** del contenedor que has creado.
4. Un pantallazo donde se vea la salida del comando `ping` para comprobar la conectividad.

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
