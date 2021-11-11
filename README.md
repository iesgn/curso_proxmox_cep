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

3. Instalación de máquinas virtuales

4. Gestionando el almacenamiento y las redes virtuales

5. Trabajo con plantillas y copias de seguridad

6. Trabajando con Linux Containers

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
