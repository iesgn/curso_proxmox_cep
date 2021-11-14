# curso_Proxmox VE_cep
Curso sobre Proxmox VE para el CEP.

## Contenidos

1. Introducción a la virtualización con Proxmox VE
    * ¿Qué es la virtualización?
    * Tipos de virtualización
    * Introducción a KVM/Qemu
    * Introducción a LXC
    * ¿Qué es Proxmox VE?
    * ¿Qué nos ofrece Proxmox VE?

2. Instalación Proxmox VE
    * Escenario real para la instalación de Proxmox VE
    * Taller de laboratorio para probar Proxmox VE
    * Instalación de Proxmox VE
    * Otras opciones de instalación
    * Acceso a Proxmox VE
    * Vista general de Proxmox VE
        * Actividad: Instalación y acceso a ProxmoxVE

3. Instalación de máquinas virtuales
    * Creación de máquinas virtuales Linux
    * Gestión de máquinas virtuales
    * Modificación de las características de las máquinas creadas
    * Creación de máquinas virtuales Windows
        * Actividad: Creación de una máquina virtual Linux
        * Actividad: Creación de una máquina virtual Windows

4. Gestionando el almacenamiento y las redes virtuales
    * Introducción al almacenamiento en Proxmox VE
    * Creación de un pool de almacenamiento para trabajar con imágenes de discos
    * Introducción a la redes virtuales en Proxmox VE
    * Creación de una red interna
        * Actividad: Creación de un pool de almacenamiento para trabajar con imágenes de discos
        * Actividad: creación de un red interna
        * Actividad: Añadir nuevos discos a una máquina virtual

5. Trabajo con plantillas y copias de seguridad
    * Clonación de máquinas virtuales
    * Convirtiendo máquinas virtuales en plantillas
    * Snapshots de máquinas virtuales
    * Copias de seguridad de máquinas virtuales
        * Actividad: Clonación de máquinas virtuales
        * Actividad: Creación de una nueva máquina virtual a partir de una plantilla
        * Actividad: Snapshot de máquinas virtuales
        * Actividad: Copia de seguridad de una máquina virtual
    * https://www.nicholasjoerger.com/blog/proxmox-ubuntu-server-18-04-golden-image

6. Trabajando con Linux Containers
    * Gestionando plantillas de contenedores
    * Creación de contenedores Linux
    * Gestión de contenedores Linux
        * Actividad: Creación de un contenedor linux

7. Gestionando Proxmox VE desde la línea de comandos

8. Gestión de usuarios en Proxmox VE

9. Aspectos avanzados

    * Trabajar con imágenes qcow2 ya existentes
    * Configuración de máquinas virtuales con cloud-init
    * Cortafuegos en Proxmox VE
    

10. Introducción al trabajo con un cluster Proxmox VE

Las tareas (desde módulo 3 hasta la 6) pueden ser la puesta en marcha de un escenario:

* Módulo 3: Se instala una máquina linux (en el pool local-pve).
* Módulo 4: Se crea un nuevo pool de almacenamiento para que las máquinas puedan utilizar imagenes qcow2 y se crea una red interna.
* Módulo 5: A partir de la máquina que instalamos en el módulo 3 se crea una plantilla desde la que se van a crear dos nuevas máquinas: router y cliente. Una se puede crear sobre local-pve, y otra sobre el pool creada en el módulo anterior. La máquina router estará conecta a la red pública y a la red privada, la máquina cliente a la red interna. Se configura la máquina router para que haga de enrutador, y de esta manera la máquina cliente tendrá acceso a internet. Todas las configuraciones de red con configuración estática.
* Módulo 6: Se crea un contenedor conectado a la red interna donde se configura un servidor DHCP, por lo que podemos cambiar la configuración de red del cliente para que se configure de forma dinámica.
