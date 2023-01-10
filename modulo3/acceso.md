# Acceso a las máquinas virtuales desde el exterior

Una vez que hemos creado las máquinas en Proxmox podemos acceder a ellas utilizando la consola de la GUI de Proxmox VE, pero es posible a ellas acceder utilizando otros protocolos específicos de acceso remoto, que suelen ser más eficiente para el trabajo con las máquinas.

## Acceso por ssh a las máquinas Linux

El protocolo más habitual para trabajar con máquinas Linux es ssh. Podemos instalar el servidor ssh durante la instalación del sistema operativo. Si no lo hemos hecho, podríamos instalarlo en distribuciones Debian/Ubuntu ejecutando:

    apt install ssh

Una vez que sabemos la ip de la máquina:

![agent](img/agent4.png)

Desde nuestro equipo podemos acceder a esta máquina por ssh indicando el nombre de usuario y la ip:

```
$ ssh jose@192.168.100.96
jose@192.168.100.96's password: 
Linux router 5.10.0-10-amd64 #1 SMP Debian 5.10.84-1 (2021-12-08) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Wed May  4 17:23:05 2022
jose@router:~$
```

## Acceso por RDP a una máquina Windows

Normalmente para acceder a las máquinas Windows usamos el protocolo RDP (Remote Desktop Protocol). Para acceder necesitamos usar un cliente RDP. Por ejemplo, en sistemas Linux puedes usar [Remmina](https://remmina.org/), si lo haces desde un sistema Windows puedes usar "Conexión a Escritorio remoto".

En este ejemplo voy a usar el cliente Remmina.

Hay que indicar que las versiones más sencillas como Windows 10 Home no tienen la posibilidad del acceso remoto, por lo tanto, vamos a utilizar una versión Windows 10 Pro. Lo primero que tenemos que hacer es configurar Windows para permitir el acceso remoto. Para ello elegimos Inicio > Configuración  > Sistema > Escritorio remoto y activa Habilitar escritorio remoto.

![acceso](img/acceso1.png)

A continuación, configuramos el cliente remmina con una nueva conexión, indicando la ip de la máquina, el usuario y la contraseña y la resolución de pantalla:

![acceso](img/acceso2.png)

Y ya podemos conectar para acceder a la máquina:

![acceso](img/acceso3.png)

* [Vídeo: Acceso a las máquinas virtuales desde el exterior](https://youtu.be/fWxsb4694iI)
