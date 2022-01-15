# Instalación de Proxmox VE

Vamos a instalar la versión 7 de Proxmox VE que está basada en la última versión estable de debian (la versión Bullseye). Aunque podríamos [instalar Proxmox en un sistema Debian 11 Bullseye](https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_11_Bullseye) ya existente, vamos a utilizar un fichero para hacer una instalación completa del sistema.

Para ello nos vamos a la [página oficial de descargas](https://www.proxmox.com/en/downloads/item/proxmox-ve-7-1-iso-installer) y nos bajamos el fichero ISO: **Proxmox VE 7.1 ISO Installer**.

Una vez que hemos preparado nuestra máquina donde vamos a hacer la instalación, comenzamos el proceso:

Comenzamos la instalación eligiendo la opción **Install Proxmox VE**.

![instalación](img/iinstalacion1.png)

Selecciona el disco donde vamos a realizar la instalación. Por defecto el disco duro se va a formatear con el sistema de ficheros *ext4*:

![instalación](img/iinstalacion2.png)

Configuramos país, la zona horario y la distribución de teclado:

![instalación](img/iinstalacion3.png)

Configuramos la contraseña del usuario `root` del sistema, con el que vamos a administrar Proxmox. Además indicamos una dirección de correo para que Proxmox nos notifique distintas informaciones.

![instalación](img/iinstalacion4.png)

Configuración de red: elegimos la interfaz de red que vamos a usar. Como hemos comentado la intefaz estará conectada a la misma red que el host (en mi caso la 192.168.100.0/24) por lo que como vemos la máquina ha tomado una IP por mi DHCP 192.168.100.94, sde indica la puerta de enlace y el servidor DNS. esta configuración también se podría poner de forma estática. También indicamos el nombre FQDN de la máquina.

![instalación](img/iinstalacion5.png)

Nos aparece un resumen de los parámetros de instalación escogidos y pulsamos sobre **Install** para comenzar la instalación.

