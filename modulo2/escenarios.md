# Escenarios para la instalación de Proxmox VE

Antes de explicar la instalación de Proxmox VE vamos a estudiar los
posibles escenarios e infraestructura donde podemos instalar Proxmox
VE.

## Instalación de Proxmox VE en nuestro centro educativo

Si queremos utilizar Proxmox VE como herramienta de virtualización
para ofrecer recursos virtualizados a los alumnos de nuestros ciclos,
tendremos que utilizar máquinas físicas con recursos suficientes:

* CPU: No es crítico, las máquinas virtuales y contenedores utilizarán
  CPU virtuales para su ejecución.
* RAM: Al crear una máquina virtual o un contenedor se irá reservando
  memoria RAM. Por lo tanto, dependiendo del tipo de sistema operativo
  que vayamos a instalar tendremos necesidades distintas.
* Almacenamiento: El almacenamiento que van a utilizar nuestras
  máquinas virtuales o contenedores podría ser proporcionado de
  distintas maneras:

    * **DAS (Direct-Attached Storage)**: Los dispositivos de
      almacenamiento están alojados en el propio servidor Proxmox VE.
    * **NAS (Network Attached Storage)**: En este caso tenemos un
      servidor de almacenamiento que nos permite compartir sistemas de
      ficheros (por ejemplo, NFS).
    * **SAN (Storage Area Network)**: En este caso, el servidor de
      almacenamiento nos permite compartir dispositivos de
      almacenamiento (de bloque) (por ejemplo, iSCSI).

Veamos a continuación dos posibles escenarios para la instalación de
Proxmox VE en nuestro centro educativo.

### Instalación de Proxmox VE en un solo nodo

Realmente Proxmox VE nos permite la construcción de un cluster de
servidores para la virtualización de recursos. En un centro educativo
puede ser una opción muy adecuada empezar a usar Proxmox con un solo
servidor. No tendríamos las características avanzadas que nos ofrece
el cluster (alta disponibilidad, migración de recursos, ...) pero
siempre podemos escalar nuestra infraestructura y crear un cluster
posteriormente. Tendríamos dos posibilidades:

**Un solo servidor Proxmox**

![escenario1](img/escenario1.drawio.png)

Utilizamos un servidor Proxmox VE conectado a la red de nuestro
departamento. Por defecto, las máquinas virtuales y contenedores
creados estarán conectadas a esta misma red, por lo que serán
accesibles sin problemas. En este caso se utilizará almacenamiento
DAS, es decir, el servidor tendrá que tener suficiente almacenamiento
local para todos los recursos virtualizados.

**Un servidor Proxmox y un servidor de almacenamiento**

![escenario2](img/escenario2.drawio.png)

En este caso tendremos dos servidores: uno para la ejecución de
recursos virtualizados (Proxmox) y otro que ofrece el
almacenamiento. En este caso el almacenamiento local del servidor
Proxmox no necesita tener gran capacidad. En este esquema se puede
ofrecer almacenamiento NAS o SAN. Por último, indicar que por seguridad
se suelen usar redes diferenciadas: la red de acceso a las máquinas
(negra) y la red de almacenamiento (roja), así los recursos de
almacenamiento no estarían disponibles de forma directa desde la red
del departamento.

### Instalación de un cluster Proxmox VE

Para sacar todo su potencial a Proxmox necesitamos instalar un cluster
de servidores. En este caso tendríamos varios servidores donde se
virtulizarían nuestros recursos. En este esquema sí sería necesario
tener un sistema de almacenamiento compartido para que los datos de
nuestros recursos virtualizados fueran compartidos entre los distintos
nodos del cluster.

![escenario3](img/escenario3.drawio.png)

Es recomendable tener una red aislada (verde) que conecte los nodos
del cluster para la gestión interna del mismo.

## Instalación de Proxmox VE en este curso

En este curso vamos a montar un laboratorio para aprender los
conceptos más importantes de Proxmox VE. Por lo tanto, os proponemos lo
siguiente:

* La instalación de **un sólo nodo de Proxmox** en una máquina virtual. El
  ámbito de este curso no nos va a permitir el estudio de un clúster
  con varios servidores Proxmox.
* La máquina virtual donde vamos a instalar Proxmox la podemos crear
  en cualquier hypervisor: **VirtualBox, VMWare, KVM, HyperV, ...**
* **Características de la máquina virtual donde vamos a realizar la instalación**
  
  Dependiendo de la cantidad de memoria RAM, espacio de disco duro y VCPU que asignemos a la máquina virtual donde vamos a instalar Proxmox VE, podremos virtualizar más o menos máquinas virtuales o contenedores:

  * Por ejemplo, desde el punto de vista de la RAM: si virtualizamos una máquina virtual sin entorno gráfico podemos asignarle 512Mb, si tiene entorno gráfico ya tendríamos que usar 1 o 2GB, si virtualizamos una máquina Windows al menos tendremos que asignar 2Gb de RAM.
  * Desde el punto de vista del almacenamiento, no es tan importante: pero tenemos que pensar que hay que almacenar las ISO para la instalación de las máquinas, los templates usados para la creación de los contenedores y los discos duros de las máquinas virtuales. Este aspectos no es tan crítico, porque cómo veremos utilizaremos *aprovisionamiento ligero* que nos permite reducir el espacio ocupado por las máquinas virtuales.
  * Al crear máquinas virtuales o contenedores podremos asignarle cores virtuales de CPU, por lo que aumentará el rendimiento si asignamos a nuestra máquina virtual suficientes núcleos de CPU.

  Por todo lo explicado a continuación la **configuración recomendada** para la máquina virtual sería:

    * **8 Gb de RAM**
    * **100 Gb de disco duro**
    * **4 núcleos de CPU**

  Podemos asignar menos recursos, pero reduciremos las posibilidades de crear muchas máquinas virtuales y contenedores. Del mismo modo,cuantos más recursos asignemos a esa máquina más máquinas virtuales y contenedores podremos crear en nuestro Proxmox.
* La máquina virtual debe tener una **interfaz de red de tipo
  "bridge"**; es decir, debe estar conectada a la misma red del
  anfitrión. Todas las máquinas virtuales y contenedores que creemos,
  por defecto, estarán conectados a la misma red.

Quien tenga la opción de utilizar una máquina física dedicada para
Proxmox puede hacerlo allí, pero no podemos considerar esta opción
como la más habitual, por lo que asumiremos que la mayoría de los
participantes utilizarán una máquina virtual en su propio equipo.

## Configuración especifica de VirtualBox para la instalación de Proxmox

Consideramos que el hipervisor más común que podemos usar para la creación de la máquina virtual donde vamos a instalar Proxmox VE es VirtualBox. Por lo tanto siguiendo estas [instrucciones](https://pve.proxmox.com/wiki/Proxmox_VE_inside_VirtualBox) tenemos que tener en cuenta los siguientes aspectos:

* Hay que habilitar la virtualización anidada: Para ello: **Sistema - Procesador - Habilitar**:

![img](img/virtualbox1.png)

* Hay que habilitar KVM como interfaz de paravirtualización y habilitar paginación anidada. Para ello: **Sistema - Aceleración**:

![img](img/virtualbox2.png)