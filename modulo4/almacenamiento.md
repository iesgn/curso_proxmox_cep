# Introducción al almacenamiento en Proxmox VE

Proxmox VE nos permite distintas **fuentes de almacenamiento** para alojar el contenido de los discos de nuestras máquinas virtuales y contenedores, y de los discos adicionales en su caso.

Según el tipo de almacenamiento que podemos configurar en nuestro
clúster, tendremos distintas características:

## Tipos de almacenamiento

Hay dos clases de almacenamiento que podemos configurar:

* **Sistemas de ficheros**: Nos permiten el acceso a un sistema de ficheros.
* **Dispositivos de bloque**: Este tipo de almacenamiento nos ofrece
      dispositivos de bloques, que posteriormente podremos formatear y
      utilizar. Un dispositivo de bloques es un dispositivo *en bruto*
      que se le ofrece a la máquina virtual para que lo gestione
      completamente. En la máquina virtual aparecerá como un disco
      duro disponible para particionar, formatear, etc.

## Almacenamiento compartido

Algunas de las **fuentes de almacenamiento** que podemos usar tienen la
característica de poder compartir la información entre distintos
nodos de nuestro clúster Proxmox VE. En el caso que utilicemos estos
tipos de almacenamiento tendremos a nuestra disposición la
funcionalidad de **migración en vivo** de máquinas virtuales y
contenedores, ya que el contenido del disco estará compartido entre
los distintos nodos del clúster. Si no tenemos esta característica, la
migración de máquinas entre distintos nodos del clúster conllevará la
copia de la imagen del disco entre los nodos.

## Snapshots

Algunas de las **fuentes de almacenamiento** que podemos usar tienen la
característica de poder realizar instantáneas (**snapshots**). De esta
manera podremos guardar el estado de un disco en un determinado
momento, y si es necesario podremos volver a ese estado a posteriori.

## Aprovisionamiento ligero

Todas las **fuentes de almacenamiento** que nos permiten la realización
de instantáneas, también nos proporcionan la funcionalidad del
**aprovisionamiento ligero**. Si utilizamos está característica la
información guardada en el almacenamiento de una máquina virtual
estará formada por una imagen base y sólo se guardará los cambios que
se van produciendo en esa máquina.

Por ejemplo,  podemos crear una máquina virtual con un disco duro de
32 GB y, después de instalar el sistema operativo invitado, el sistema
de archivos raíz de la máquina virtual contiene 3 GB de datos. En ese
caso, solo se escriben 3 GB en el almacenamiento, aunque la máquina
virtual ve un disco duro de 32 GB.

De esta manera tendremos mucho ahorro en espacio ocupado de
almacenamiento y sobre todo el almacenamiento realmente usado por las
máquinas virtuales será el que se ocupe en Proxmox, no hay reserva
previa de almacenamiento.

## Resumen de los tipos de las fuentes de almacenamiento

|Nombre   |Tipo   |Compartido|Instantáneas / P.L.|
|---------|-------|:--------:|:-------------:|
|ZFS (local)|Sist. Ficheros|No|Si|
|Directory|Sist. Ficheros|No|No (Si, con ficheros qcow2)|
|BTRFS|Sist. Ficheros|No|Si|
|NFS|Sist. Ficheros|Si|No (Si, con ficheros qcow2)|
|CIFS|Sist. Ficheros|Si|No (Si, con ficheros qcow2)|
|Proxmox Backup|Sist. Ficheros / Disp. Bloque|Si|No|
|GlusterFS|Sist. Ficheros|Si|No (Si, con ficheros qcow2)|
|CephFS|Sist. Ficheros|Si|Si|
|LVM|Disp. Bloque|No (Si, usando iSCSI)|No|
|LVM-thin|Disp. Bloque|No|Si|
|iSCSI|Disp. Bloque|Si|No|
|Ceph/RBD|Disp. Bloque|Si|Si|
|ZFS over iSCSI|Disp. Bloque|Si|Si|

## ¿Qué podemos guardar en las distintas fuentes de almacenamiento?

En cada tipo de fuente de almacenamiento se puede guardar información de
distintos tipos:

* **Disk image**: Imágenes de discos para las máquinas virtuales.
* **Containers**: Sistema de ficheros de los contenedores Linux.
* **ISO image**: Imágenes ISO.
* **Container template**: Plantillas de contenedores.
* **VZDump backup files**: Ficheros de copia de seguridad.
* ...

## Conclusión

En este tema vamos a profundizar en los tipos de almacenamiento más
sencillos de gestionar: el tipo **Directory** y el tipo **LVM**. 

Para profundizar en los distintos tipos de almacenamiento que podemos usar
en Proxmox VE: [Proxmox VE Storage](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#chapter_storage).


