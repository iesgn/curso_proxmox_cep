# Creación de un pool de almacenamiento tipo Directory

El almacenamiento de tipo *Directory* nos posibilita guardar información en un nodo del cluster Proxmox VE. Por lo tanto no tenemos la funcionalidad de datos compartidos.

## Pool de almacenamiento configurado por defecto

![storage_local](img/storage_local.png)

Como vimos anteriormente, al instalar Proxmox VE se nos crea un pool de almacenamiento de tipo *Directory* llamado **local**. La información guardada en este pool se guarda en el directorio `/var/lib/vz` y por defecto esta configurado para guardar en él lo siguiente:

* **ISO image**: Imágenes ISO.
* **Container template**: Plantillas de contenedores.
* **VZDump backup files**: Ficheros de copia de seguridad.

![storage_local](img/storage_local2.png)

Si elegimos el almacenamiento **local**, podemos ver los datos que podemos guardar:

![storage_local](img/storage_local3.png)

Si accedemos al nodo por ssh (o desde la terminal del panel de control, opción *Shell*), podemos comprobar la estructura de directorios que se ha creado:

```bash
ssh root@192.168.100.87
...
root@pve:~# cd /var/lib/vz
root@pve:/var/lib/vz# ls
dump  images  template
```

Por ejemplo las imágenes ISO se guardan en:

```bash
root@pve:/var/lib/vz# cd template/iso/
root@pve:/var/lib/vz/template/iso# ls
debian-11.1.0-amd64-netinst.iso  ubuntu-20.04.3-desktop-amd64.iso  virtio-win-0.1.208.iso  Win10_21H1_Spanish_x64.iso
```

## Creación de un nuevo pool de almacenamiento de tipo Directory

Podríamos modificar el pool de almacenamiento anterior y añadir dos nuevos tipos de informaciones que podría almacenar:

* **Disk image**: Imágenes de discos para las máquinas virtuales.
* **Containers**: Sistema de ficheros de los contenedores Linux.

Sin embargo, vamos a aprender a crear otro pool de almacenamiento donde vamos a guardar las imágenes de disco de las máquinas virtuales y los datos del sistema de fichero de los contenedores.

Los discos de imágenes de las máquinas virtuales se pueden guardar en dos tipos de ficheros de imágenes:

* **raw**: El formato raw es una imagen binaria sencilla de la imagen del disco. Se ocupa todo el espacio que hayamos indicado al crearla. El acceso es más eficiente.
* **qcow2**: El formato QEMU copy-on-write. Al crearse sólo se ocupa el espacio que se está ocupando con los datos, el fichero irá creciendo cuando escribamos en el él. Acepta snapshots y aprovisionamiento ligero. Es menos eficiente en cuanto al acceso. 
* **vmdk**: Un formato de archivo abierto, creado por VMware.

Para crear el nuevo pool, elegimos *Datacenter->Storage->Add->Directory*:

![storage_directory](img/storage_directory.png)

Indicamos un nombre, el directorio y el contenido que vamos a guardar, en nuestros caso: **Disk image** y **Containers**.

![storage_directory](img/storage_directory2.png)

**Nota: El directorio `/var/lib/images` se crea automáticamente.**

## Creación de una máquina virtual usando el nuevo pool de almacenamiento

Ahora podemos crear máquinas virtuales cuyos discos virtuales se guarden en ficheros de imágenes que se guardarán en el pool de almacenamiento **local-images**.

Durante el proceso de creación de la imagen, podremos elegir el pool de almacenamiento donde vamos a guardar el disco, en nuestro caso elegimos el pool **local-images**, y el tipo de fichero de imagen, nosotros vamos a elegir qcow2:

![storage_directory](img/storage_directory3.png)

Hemos creado y configurado la máquina virtual con ID 101, si accedemos al no podemos ver donde se ha creado el fichero de imagen:

```bash
root@pve:/var/lib/images/images/101# ls
vm-101-disk-0.qcow2
```

**Nota: El pool de almacenamiento de tipo *Directory* lo hemos creado sobre el disco de la máquina donde tenemos instalado Proxmox VE, por lo tanto su capacidad será la que tiene este disco. En circunstancias reales, el pool de tipo *Directory* lo podríamos crear sobre un dispositivo de bloque (disco, raid,...) añadido al nodo Proxmox VE.**

