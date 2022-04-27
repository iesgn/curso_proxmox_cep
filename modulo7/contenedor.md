# Creación de contenedores Linux

Después de descargar las plantillas de contenedores con als que vamos a trabajar, estamos en disposición de crear un contenedor LXC. En este apartado vamos a explicar la creación de una contenedor LXC. Sólo indicaremos las opciones más básicas para su creación.

Elegimos la opción de crar un contenedor LXC:

**Imágen de crate LXC**

Y seguimos los siguientes pasos:

## Identificar el contenedor LXC

Indicamos el nodo donde se va a crear la máquina, su ID y su nombre. Además tendremos que indicar la contraseña de acceso para el usuario root del contenedor o indicar nuestra clave ssh pública para el acceso al contenedor.

**Imagen 1 lxc**

## Elegimos la plantilla 

Elegimos la plntilla desde la que vamos a crear el contenedor entre las que hemos descargado anteriormente. La plantilla se escogerá del medio de almacenamiento *local*. 

**Imagen 2 lxc**

## Selección del disco

En este apartado seleccionamos la configuración del disco raíz del contenedor que vamos a crear. Elegimos el medio de almacenamiento para almacenar el disco, por ejemplo *local-pve*, (en este caso el disco de la máquina se guardará en un volumen lógico). También indicaremos el tamaño del disco.

**Imagen 3 lxc**

## Selección de la CPU

Seleccionamos el número de cores de vCPU que va a usar el contenedor.

**Imagen 4 lxc**

## Configuración de la memoria

Indicamos la cantidad de memoria que tendrá nuestra máquina virtual (en MiB no MB (!)).

**Imagen 5 lxc**

## Configuración de red

En un principio nuestra máquina estará conectada al bridge externo *vmbr0*  y la tarjeta de red se llamará *eth0*. Esta configuración se puede cambiar, y podríamos conectar nuestro contendor a una bridge software definido por nosotros. Además tendremos que decidir si la configuración de red será automática (DHCP) o manuel, indicando la dirección (con formato IPv4/CIDR) y la puerta de enlace.

**Imagen 6 lxc**

## Configuración DNS

En el último paso podemos configurar los servidores DNS que va a utilizar el contenedor o dejarlo si rellenar, con lo que utilizará los DNS definido en el servidor Proxmox.

**Imagen 7 lxc**

## Utilización del contenedor

Una vez que se ha creado el contenedor, podemos inciarlo y acceder a él por medio de la consola:

**Imagen inicio de contenedor**

**Imagen consola contenedor**