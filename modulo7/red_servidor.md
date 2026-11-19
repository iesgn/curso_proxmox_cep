# Configuración de la red del servidor Proxmox VE

La configuración de red en Proxmox VE se ofrece a nivel de servidor (es decir, cada nodo que forma el clúster tendrá su configuración de red). En nuestro caso, como solo tenemos un nodo, podemos obtener la configuración inicial de red a nivel del servidor, en la opción **System - Network** del nodo:

![img](img/red1.png)

En este curso hemos instalado Proxmox VE sobre una máquina virtual, y en nuestro escenario nos aparecen los siguientes recursos:

* **La interfaz del servidor Proxmox (en el ejemplo, nic0)**: Corresponde a la interfaz del servidor. Desde Proxmox VE 9 el instalador fija el nombre de las interfaces (**nic0**, **nic1**, ...) para que no cambie al actualizar el sistema o el hardware. En la columna **Alternative Names** vemos otros nombres de la misma interfaz.
* **Un Linux Bridge (vmbr0)**: A este bridge está conectada la interfaz del servidor y tiene la IP que indicamos durante la instalación, configurada de forma estática (en mi caso la `192.168.122.235`). Esta ip corresponde a la IP del servidor y es la que utilizo para acceder a la página web de Proxmox.

Por defecto las máquinas virtuales y contenedores que estamos creando se conectan a este Linux Bridge, y tomarán direccionamiento del router físico, en mi caso el direccionamiento será el `192.168.122.0/24`. Por lo tanto, todas las máquinas gestionadas por Proxmox serán accesibles desde cualquier ordenador de mi red local.

El esquema que tenemos sería el siguiente:

![img](img/red2.png)

En una instalación real de Proxmox el servidor puede tener más interfaces de red, podría existir un switch físico en la infraestructura y podríamos necesitar una configuración más avanzada usando por ejemplo **Bonding** (Link Aggregation) o **VLAN**. Proxmox VE nos permite configurar estas opciones avanzadas usando **Linux Bridge** o **Open vSwitch** (otra tecnología que nos permite trabajar con switch software; para usarla hay que instalar el paquete `openvswitch-switch`). En este curso no se va a abordar el estudio de estas características avanzadas.

![img](img/red3.png)

## Conexión de las máquinas virtuales/contenedores al bridge vmbr0

Como hemos indicado anteriormente, por defecto, las máquinas virtuales y contenedores que hemos creado en nuestro servidor se conectan al bridge **vmbr0**, por lo tanto, se configurarán de forma automática usando el servidor DHCP de nuestra infraestructura, en nuestro caso el del router físico.

![img](img/red4.png)

Y podemos comprobar que ha tomado una ip en el direccionamiento que reparte nuestro servidor DHCP:

![img](img/red5.png)

Por lo que podemos acceder a ella desde cualquier equipo conectado a nuestra red local.

* [Vídeo: Configuración de la red del servidor Proxmox VE](https://youtu.be/SlFlWYywE0Y)
