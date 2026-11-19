# Añadir nuevos discos a una máquina virtual

En el apartado *Hardware* de cualquier máquina virtual podemos añadirle nuevos discos duros con la opción **Add → Hard Disk** (la opción **Import Hard Disk** sirve para añadir un disco a partir de una imagen que ya tengamos):

![new_disco](img/new_disco.png)

Al añadir el nuevo disco, tendremos que elegir en qué fuente de almacenamiento se va a guardar su información y el tamaño del disco:

![new_disco](img/new_disco2.png)

En nuestro caso, tenemos disponibles dos fuentes de almacenamiento:

* **local-images**: De tipo `Directory`, la información del disco se guardará en un fichero de imagen.
* **local-lvm**: De tipo `LVM-Thin`, la información del disco se guardará en un volumen LVM.

En nuestro caso vamos a elegir la opción **local-images**, por lo que tendremos que elegir el tipo de fichero de imagen que vamos a usar:

![new_disco](img/new_disco3.png)

Al añadir comprobamos que la máquina tiene dos discos:

![new_disco](img/new_disco4.png)

## Formateo y uso del disco en la máquina virtual

Si accedemos a la máquina virtual (podemos hacerlo desde la terminal de Proxmox, opción `Shell` o accediendo a la máquina por ssh), podemos comprobar que tenemos un nuevo disco:

```bash
ssh usuario@192.168.122.22
...
usuario@debian:~$ su -
root@debian:~# lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   32G  0 disk 
├─sda1   8:1    0   31G  0 part /
├─sda2   8:2    0    1K  0 part 
└─sda5   8:5    0 1022M  0 part [SWAP]
sdb      8:16   0    1G  0 disk 
sr0     11:0    1  756M  1 rom  
```

Podemos formatear el disco:

```bash
root@debian:~# mkfs.ext4 /dev/sdb
```

Y montar el disco para su utilización:

```bash
root@debian:~# mount /dev/sdb /mnt
```

Podemos ver las características del disco montado:

```bash
root@debian:~# df -h
S.ficheros     Tamaño Usados  Disp Uso% Montado en
udev             456M      0  456M   0% /dev
tmpfs             97M   472K   97M   1% /run
/dev/sda1         31G   1,2G   28G   5% /
tmpfs            484M      0  484M   0% /dev/shm
tmpfs            5,0M      0  5,0M   0% /run/lock
tmpfs            484M      0  484M   0% /tmp
tmpfs             97M   8,0K   97M   1% /run/user/1000
/dev/sdb         974M   280K  906M   1% /mnt
```

* [Vídeo: Añadir nuevos discos a una máquina virtual](https://youtu.be/hOZpZhkjlUE)


