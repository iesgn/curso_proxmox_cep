# Creación de una fuente de almacenamiento de tipo Directory

El almacenamiento de tipo **Directory** nos posibilita guardar información en un nodo del clúster Proxmox VE. Por lo tanto, no tenemos la funcionalidad de datos compartidos.

## Fuente de almacenamiento configurado por defecto

![storage_local](img/storage_local.png)

Como vimos anteriormente, al instalar Proxmox VE se nos crea una fuente de almacenamiento de tipo *Directory* llamado **local**. La información guardada en esta fuente se guarda en el directorio `/var/lib/vz` y por defecto está configurado para guardar en él lo siguiente:

* **ISO image**: Imágenes ISO.
* **Container template**: Plantillas de contenedores.
* **Backup**: Ficheros de copia de seguridad.
* **Import**: Imágenes de discos y ficheros OVA para importar máquinas virtuales.

![storage_local](img/storage_local2.png)

Si elegimos el almacenamiento **local**, podemos ver los datos que podemos guardar:

![storage_local](img/storage_local3.png)

Si accedemos al nodo por ssh (o desde la terminal del panel de control, opción *Shell*), podemos comprobar la estructura de directorios que se ha creado:

```bash
ssh root@192.168.122.235
...
root@pve:~# cd /var/lib/vz
root@pve:/var/lib/vz# ls
dump  images  import  template
```

Por ejemplo, las imágenes ISO se guardan en:

```bash
root@pve:/var/lib/vz# cd template/iso/
root@pve:/var/lib/vz/template/iso# ls
debian-13.7.0-amd64-netinst.iso  virtio-win.iso  Win11_25H2_Spanish_x64_v2.iso
```

## Creación de una nueva fuente de almacenamiento de tipo Directory

Podríamos modificar la fuente de almacenamiento anterior y añadir dos nuevos tipos de informaciones que podría almacenar:

* **Disk image**: Imágenes de discos para las máquinas virtuales.
* **Containers**: Sistema de ficheros de los contenedores Linux.

Sin embargo, vamos a aprender a crear otra fuente de almacenamiento donde vamos a guardar las imágenes de disco de las máquinas virtuales y los datos del sistema de fichero de los contenedores.

Los discos de imágenes de las máquinas virtuales se pueden guardar en tres tipos de ficheros de imágenes:

* **raw**: El formato raw es una imagen binaria sencilla de la imagen del disco. Se ocupa todo el espacio que hayamos indicado al crearla. El acceso es más eficiente.
* **qcow2**: El formato QEMU copy-on-write. Al crearse sólo se ocupa el espacio que se está ocupando con los datos, el fichero irá creciendo cuando escribamos en él. Acepta snapshots y aprovisionamiento ligero. Es menos eficiente en cuanto al acceso. 
* **vmdk**: Un formato de archivo abierto, creado por VMware.

Para crear la nueva fuente, elegimos *Datacenter->Storage->Add->Directory*:

![storage_directory](img/storage_directory.png)

Indicamos un nombre, el directorio y el contenido que vamos a guardar, en nuestro caso: **Disk image** y **Containers**.

![storage_directory](img/storage_directory2.png)

**Nota: El directorio `/var/lib/images` se crea automáticamente.**

Si marcamos la casilla **Advanced**, aparecen dos opciones más: **Preallocation**, que indica si se reserva el espacio de los ficheros de imagen al crearlos, y **Allow Snapshots as Volume-Chain**, la novedad de Proxmox VE 9 que vimos en el apartado anterior. Como todavía está en pruebas, la dejamos desmarcada.

## Creación de una máquina virtual usando la nueva fuente de almacenamiento

Ahora podemos crear máquinas virtuales cuyos discos virtuales se guarden en ficheros de imágenes que se guardarán en la fuente de almacenamiento **local-images**.

Durante el proceso de creación de la máquina, en la pestaña **Disks**, podremos elegir la fuente de almacenamiento donde vamos a guardar el disco, en nuestro caso elegimos la fuente **local-images**, y el tipo de fichero de imagen. Al elegir una fuente de tipo *Directory* el formato por defecto es qcow2, que es el que vamos a usar:

![storage_directory](img/storage_directory3.png)

Hemos creado y configurado la máquina virtual con ID 102, si accedemos al nodo podemos ver donde se ha creado el fichero de imagen:

```bash
root@pve:/var/lib/images/images/102# ls
vm-102-disk-0.qcow2
```

**Nota: La fuente de almacenamiento de tipo *Directory* la hemos creado sobre el disco de la máquina donde tenemos instalado Proxmox VE, por lo tanto,  su capacidad será la que tiene este disco. En circunstancias reales, la fuente de tipo *Directory* la podríamos crear sobre un dispositivo de bloque (disco, raid, ...) añadido al nodo Proxmox VE.**

* [Vídeo: ](https://youtu.be/eXDjL2FJX_o)
