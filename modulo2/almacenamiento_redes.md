# Almacenamiento y redes disponibles

Cuando instalamos Proxmox VE tenemos a nuestra disposición algunos recursos ya creados:

## Almacenamiento

![almacenamiento](img/almacenamiento.png)

Por defecto tenemos creados dos objetos de almacenamiento:

### local

Es una almacenamiento de tipo *Directory* y por defecto en este almacenamiento se podrán guardar:

* Ficheros de copia de seguridad
* Imágenes ISO
* Plantillas de contenedores

Al ser tipo *Directory* esta información se guardará en un directorio del nodo, en concreto se guardará en `/var/lib/vz`.

### local-lvm

Es un almacenamiento de tipo *LVM-Thin*, en él se podrán guardar:

* Imágenes de discos para las máquinas virtuales
* Imágenes de discos para contenedores Linux

Cuando creemos una máquina virtual o un contenedor los ficheros de su disco se guardarán en un volumen lógico LVM de un grupo de volumenes de tipo *LVM-Thin*, en este caso el volumen lógico creado no ocupará todo el espacio desde el principio, ira creciendo según vayamos creando y modificando ficheros.

Hay muchos tipos de objetos de almacenamiento, su creación y configuración lo veremos en el módulo correspondiente.

## Redes virtuales

![redes](img/redes.png)

Por defecto, al instalar Proxmox VE, tenemos configurada una red pública:

* `enp1s0`: Es la interfaz física del nodo.
* `vmbr0`: Es un *Linux Breidge* al que está conectado el nodo. En este switch se conectarán, por defecto, las máquinas virtuales y contenedores que vamos a crear, que tomarán direccionamiento del servidor DHCP de nuestra infraestructura y que tomarán una dirección IP con el mismo direccionamiento que el nodo, por lo que serán accesible desde nuestro cliente.

En mi caso, la red que tengo configurada tendrá direccionamiento `192.168.100.0/24` y la puerta de acceso es la `192.168.100.1`.

Evidentemente, podremos crear más redes. Su creación y configuración lo estudiaremos en el módulo correspondiente del curso.
