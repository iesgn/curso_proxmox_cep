# Introducción al almacenamiento en Proxmox VE

Proxmox VE nos permite distintas fuentes de almacenamientos (**pools de almmacenamiento**) para almacenar el contenido de los discos de nuestras máquinas virtuales y contenedores, y de los discos adicionales que podemos conectarles.

Según el tipo de almacenamientos que podemos configurar en nuestro cluster, tendremos distintas características:

1. **Tipos de almacenamiento**

    Hay dos clases de almacenamiento que podemos configurar:

    * **Sistemas de ficheros**: Nos permiten el acceso a un sistema de ficheros.  
    * **Dispositivos de bloque**: Este tipo de almacenamiento nos ofrece dispositivos de bloques, que posteriormente podremos formatear y utilizar.

2. **Almacenamiento compartido**

    Algunos de los **pools de almacenamientos** que podemos usar tienen la características de poder compartir la información entre distintos nodos de nuestro cluster Proxmox VE. En el caso que utilicemos estos tipos de almacenamiento tendremos a nuestra disposición la funcionalidad de **migración en vivo** de máquinas virtuales y contenedores, ya que el contenido del disco estará compartido entre los distintos nodos del cluster. Si no tenemos esta característica, la migración de máquinas entre distintos nodos del cluster conllevará la copia de la imagen del disco entre los nodos.

3. **Snapshots**

    Algunos de los **pools de almacenamientos** que podemos usar tienen la característica de poder realizar un **snapshot**. De esta manera podremos guardar el estado de un disco en un determinado momento, y si es necesario podremos volver a ese estado en un determinado momento.

4. **Aprovisionamiento ligero**

    Todos los **pools de almacenamiento** que nos permiten la realización de snapshots, también nos proporcionan la funcionalidad del **aprovisionamiento ligero**. Si utilizamos está característica la información guardada en el almacenamiento de una máquina virtual estará formada por una imagen base y sólo se guardará los cambios que se van produciendo en esa máquina.

    Por ejemplo,  podemos crear una máquina virtual con un disco duro de 32 GB y, después de instalar el sistema operativo invitado, el sistema de archivos raíz de la máquina virtual contiene 3 GB de datos. En ese caso, solo se escriben 3 GB en el almacenamiento, aunque la máquina virtual ve un disco duro de 32 GB.

    De esta manera tendremos mucho ahorro en espacio ocupado de almacenamiento.

## Resumen de los tipos de los pools de almacenamiento

|Nombre   |Tipo   |Compartido|Snapshots / P.L.|
|---------|-------|:--------:|:-------------:|
|ZFS (local)|Sist. Archivo|No|Si|
|Directorio|Sist. Archivo|No|No (Si, con ficheros qcow2)|
|BTRFS|Sist. Archivo|No|Si|
|NFS|Sist. Archivo|Si|No (Si, con ficheros qcow2)|
|CIFS|Sist. Archivo|Si|No (Si, con ficheros qcow2)|
|Proxmox Backup|Sist. Archivo / Disp. Bloque|Si|No|
|GlusterFS|Sist. Archivo|Si|No (Si, con ficheros qcow2)|
|CephFS|Sist. Archivo|Si|Si|
|LVM|Disp. Bloque|No (Si, usando iSCSI)|No|
|LVM-thin|Disp. Bloque|No|Si|
|iSCSI|Disp. Bloque|Si|No|
|Ceph/RBD|Disp. Bloque|Si|Si|
|ZFS over iSCSI|Disp. Bloque|Si|Si|

## ¿Qué podemos guardar en los distintos pools de almacenamiento?

En cada tipo de pool de almacenamiento se puede guardar información de distintos tipo:

* **Disk image**: Imágenes de discos para las máquinas virtuales.
* **Containers**: Sistema de ficheros de los contenedores Linux.
* **ISO image**: Imágenes ISO.
* **Container template**: Plantillas de contenedores.
* **VZDump backup files**: Ficheros de copia de seguridad.
* ...

## Conclusión

En este tema vamos a profundizar en los tipos de almacenamientos más sencillos de gestionar: el tipo **Directorio** y el tipo **LVM**. Para profundizar en los distintos tipos de almacenamiento que podemos usar en Proxmox VE: [Proxmox VE Storage](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#chapter_storage).


