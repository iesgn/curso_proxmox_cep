# Acceso a las máquinas virtuales desde el exterior

Una vez que hemos creado las máquinas en Proxmox podemos acceder a ellas utilizando la consola de la GUI de Proxmox VE, pero es posible a ellas acceder utilizando otros protocolos específicos de acceso remoto, que suelen ser más eficiente para el trabajo con las máquinas.

## Acceso por ssh a las máquinas Linux

El protocolo más habitual para trabajar con máquinas Linux es ssh. Podemos instalar el servidor ssh durante la instalación del sistema operativo. Si no lo hemos hecho, podríamos instalarlo en distribuciones Debian/Ubuntu ejecutando:

    apt install ssh

Una vez que sabemos la ip de la máquina:

![agent](img/agent4.png)

Desde nuestro equipo podemos acceder a esta máquina por ssh indicando el nombre de usuario y la ip:

```
$ ssh usuario@192.168.122.22
usuario@192.168.122.22's password: 
Linux debian 6.12.117+deb13-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.12.117-1 (2026-11-12) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu Nov 19 10:25:05 2026 from 192.168.122.1
usuario@debian:~$
```

## Acceso por RDP a una máquina Windows

Normalmente para acceder a las máquinas Windows usamos el protocolo RDP (Remote Desktop Protocol). Para acceder necesitamos usar un cliente RDP. Por ejemplo, en sistemas Linux puedes usar [Remmina](https://remmina.org/), si lo haces desde un sistema Windows puedes usar "Conexión a Escritorio remoto".

En este ejemplo voy a usar el cliente Remmina.

Hay que indicar que las versiones más sencillas como Windows 11 Home no tienen la posibilidad del acceso remoto, por lo tanto, vamos a utilizar una versión Windows 11 Pro (también lo permiten las ediciones Enterprise y Education). Lo primero que tenemos que hacer es configurar Windows para permitir el acceso remoto. Para ello elegimos Inicio > Configuración > Sistema > Escritorio remoto, activamos la opción *Escritorio remoto* y confirmamos.

![acceso](img/acceso1.png)

A continuación, configuramos el cliente remmina con una nueva conexión de tipo RDP, indicando la ip de la máquina, el usuario y la contraseña:

![acceso](img/acceso2.png)

Y ya podemos conectar para acceder a la máquina. La primera vez que nos conectemos tendremos que aceptar el certificado del equipo Windows:

![acceso](img/acceso3.png)

* [Vídeo: Acceso a las máquinas virtuales desde el exterior](https://youtu.be/fWxsb4694iI)
