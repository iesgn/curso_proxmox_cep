# Preparando un laboratorio para testear Proxmox VE

En este curso vamos a montar un laboratorio para aprender los
conceptos más importantes de Proxmox VE. Por lo tanto, os proponemos lo
siguiente:

* La instalación de **un sólo nodo de Proxmox** en una máquina virtual. El
  ámbito de este curso no nos va a permitir el estudio de un clúster
  con varios servidores Proxmox.
* La máquina virtual donde vamos a instalar Proxmox la podemos crear
  en cualquier hipervisor: **VirtualBox, VMWare, KVM, HyperV, ...**. Aunque en este curso vamos a suponer que elegimos VirtualBox como hipervisor más utilizado.

## Configuración de la máquina virtual donde realizaremos la instalación
  
  Dependiendo de la cantidad de memoria RAM, espacio de disco duro y VCPU que asignemos a la máquina virtual donde vamos a instalar Proxmox VE, podremos virtualizar más o menos máquinas virtuales o contenedores:

  * Por ejemplo, desde el punto de vista de la RAM: si virtualizamos una máquina virtual sin entorno gráfico podemos asignarle 512Mb, si tiene entorno gráfico ya tendríamos que usar 1 o 2GB, si virtualizamos una máquina Windows al menos tendremos que asignar 4Gb de RAM.
  * Desde el punto de vista del almacenamiento: Este factor no es tan importante, pero tenemos que pensar que hay que almacenar las ISO para la instalación de las máquinas, las plantillas (templates) usadas para la creación de los contenedores, las copias de seguridad de las máquinas, ... y los discos duros de las máquinas virtuales. Este aspecto no es tan crítico, porque cómo veremos utilizaremos *aprovisionamiento ligero* que nos permite reducir el espacio ocupado por las máquinas virtuales.
  * Al crear máquinas virtuales o contenedores podremos asignarle cores virtuales de CPU, por lo que aumentará el rendimiento si asignamos a nuestra máquina virtual suficientes núcleos de CPU.

Por todo lo explicado a continuación la **configuración recomendada** para la máquina virtual sería:

* **8 Gb de RAM**
* **100 Gb de disco duro**
* **4 núcleos de CPU**

Podemos asignar menos recursos, pero reduciremos las posibilidades de crear muchas máquinas virtuales y contenedores. Del mismo modo, cuantos más recursos asignemos a esa máquina más máquinas virtuales y contenedores podremos crear en nuestro Proxmox.

La máquina virtual debe tener una **interfaz de red de tipo "bridge"**; es decir, debe estar conectada a la misma red del
  anfitrión. Todas las máquinas virtuales y contenedores que creemos, por defecto, estarán conectados a la misma red.

Quien tenga la opción de utilizar una máquina física dedicada para
Proxmox puede hacerlo allí, pero no podemos considerar esta opción
como la más habitual, por lo que asumiremos que la mayoría de los
participantes utilizarán una máquina virtual en su propio equipo.

## Configuración especifica de VirtualBox para la instalación de Proxmox

Consideramos que el hipervisor más común que podemos usar para la creación de la máquina virtual donde vamos a instalar Proxmox VE es VirtualBox. Para esta configuración se ha usado la versión **7.2** (puedes descargarla desde la [página oficial de VirtualBox](https://www.virtualbox.org/wiki/Downloads)). En versiones anteriores puede que no exista alguna configuración o se encuentre modificada. La interfaz de VirtualBox es la misma en Linux, Windows y macOS, por lo que las capturas de pantalla te servirán independientemente del sistema operativo de tu equipo. Por lo tanto siguiendo estas [instrucciones](https://pve.proxmox.com/wiki/Proxmox_VE_inside_VirtualBox) tenemos que tener en cuenta los siguientes aspectos:

**Nota:** En VirtualBox 7 la ventana de **Configuración** de la máquina tiene dos modos: **Basic** y **Expert**. Para ver todas las opciones que vamos a indicar a continuación tenemos que elegir el modo **Expert**. Además, algunas opciones aparecen en inglés aunque tengamos VirtualBox en español.

### Configuraciones necesarias

* Hay que habilitar la virtualización anidada: Para ello: **Sistema - Procesador**, opción **Nested VT-x/AMD-V**:

![img](img/virtualbox1.png)

* Hay que habilitar KVM como interfaz de paravirtualización y habilitar paginación anidada. Para ello: **Sistema - Aceleración**, opciones **Paravirtualization Interface: KVM** y **Nested Paging**:

![img](img/virtualbox2.png)

* Hay que configurar la red de la máquina en modo **Adaptador puente** y habilitar el **[modo promiscuo](https://es.wikipedia.org/wiki/Modo_promiscuo)** (opción **Promiscuous Mode: Permitir todo**). Es recomendable que el adaptador puente utilice una interfaz física cableada para la conexión. Si conectamos el adaptador puente con una conexión wifi podemos experimentar problemas, ya que la mayoría de las tarjetas wifi no soportan el **modo promiscuo**.

![img](img/virtualbox3.png)

### Configuraciones recomendadas

Estas configuraciones son recomendadas para aumentar el rendimiento de la máquina virtual donde vamos a instalar Proxmox y de esta forma intentar mitigar el descenso de rendimiento en las máquinas creadas en el sistema a causa de la virtualización anidada que estamos haciendo.

* Al crear el disco duro de la máquina, en el asistente de creación de la máquina virtual (apartado **Specify virtual hard disk**), marcar la opción **Reservar completamente**. Normalmente creamos discos que se reservan dinámicamente, donde va creciendo el espacio ocupado según las necesidades. Si reservamos inicialmente todo el espacio del disco aumentaremos el rendimiento.

![img](img/virtualbox4.png)

* Usar dispositivos paravirtualizados, que ofrecen más rendimiento que otros modelos que están emulados. En la configuración del almacenamiento, el disco duro debe estar conectado a un controlador de tipo **virtio-scsi**:

![img](img/virtualbox5.png)

* Del mismo modo, el tipo de la interfaz de red (**Tipo de Adaptador**) será **Red paravirtualizada (virtio-net)**:

![img](img/virtualbox6.png)

## Si usas Windows como sistema anfitrión

Si tu equipo usa Windows hay que tener en cuenta que si está activo el hipervisor de Windows (**Hyper-V**), VirtualBox funcionará por encima de él (lo notarás porque aparece el icono de una tortuga verde en la barra de estado de la máquina virtual). En ese caso **la virtualización anidada no funcionará** y Proxmox VE no podrá ejecutar máquinas virtuales.

Hyper-V se activa, por ejemplo, si usamos **WSL2**, **Docker Desktop** o **Windows Sandbox**. Para desactivarlo:

* En **Activar o desactivar las características de Windows** desmarcamos **Hyper-V**, **Plataforma de máquina virtual** y **Plataforma del hipervisor de Windows**.
* En **Seguridad de Windows - Seguridad del dispositivo - Aislamiento del núcleo** desactivamos la **Integridad de memoria**.
* Si sigue sin funcionar, ejecutamos en una terminal de administrador `bcdedit /set hypervisorlaunchtype off`.
* Finalmente, reiniciamos el equipo.

## Si usas un Mac con procesador Apple (M1, M2, ...)

VirtualBox en los equipos Mac con procesadores Apple solo puede ejecutar sistemas operativos para la arquitectura ARM y no ofrece virtualización anidada, por lo que no podrás seguir el curso de esta manera. En este caso necesitarás utilizar un equipo con procesador Intel o AMD.

* [Vídeo: Preparando un laboratorio para testear Proxmox VE](https://youtu.be/DVTuTRJcTGY)
