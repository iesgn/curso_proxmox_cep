# Curso PROXMOX VE
Curso sobre Proxmox VE para el CEP.

## Contenidos

1. Introducción a la virtualización con Proxmox VE
    * [¿Qué es la virtualización?](modulo1/virtualizacion.md)
    * [Tipos de virtualización](modulo1/tipos.md)
    * [Introducción a Proxmox VE](modulo1/proxmox.md)
        * Actividad 1.1: ¿Qué experiencia previa tenemos de virtualización?
    
2. Instalación de Proxmox VE
    * [Escenarios para la instalación de Proxmox VE](modulo2/escenarios.md)
    * [Preparando un laboratorio para testear Proxmox VE](modulo2/laboratorio.md)
    * [Instalación de Proxmox VE](modulo2/instalacion.md)
    * [Acceso a la GUI de Proxmox VE](modulo2/acceso.md)
    * [Vista general de la GUI de Proxmox VE](modulo2/vista_general.md)
    * [Introducción al clúster Proxmox VE](modulo2/introduccion_cluster.md)
    * [Almacenamiento y redes disponibles](modulo2/almacenamiento_redes.md)
        * [Actividad 2.1: Instalación y acceso a Proxmox VE (OBLIGATORIA)](modulo2/actividad1.md)

3. Instalación de máquinas virtuales
    * [Gestión de imágenes ISO](modulo3/iso.md)
    * [Dispositivos paravirtualizados](modulo3/paravirtualizados.md)
    * [Creación de máquinas virtuales Linux](modulo3/creacion_linux.md)
    * [Gestión de máquinas virtuales](modulo3/gestion.md)
    * [Características y hardware de las máquinas virtuales](modulo3/caracteristicas.md)
    * [Creación de máquinas virtuales Windows](modulo3/creacion_windows.md)
    * [Instalación de Qemu-guest-agent en las máquinas virtuales](modulo3/agent.md)
        * [Actividad 3.1: Creación de una máquina virtual Linux (OBLIGATORIA)](modulo3/actividad1.md)
        * [Actividad 3.2: Creación de una máquina virtual Windows (OBLIGATORIA)](modulo3/actividad2.md)
        * Actividad 3.3: Instalación de servicios en una máquina virtual (VOLUNTARIA)
        ...
        * [Actividad 3.3: Creación de un escenario  de trabajo (1ª parte) (VOLUNTARIA)](modulo3/actividad3.md)

4. Gestionando el almacenamiento
    * [Introducción al almacenamiento en Proxmox VE](modulo4/almacenamiento.md)
    * [Creación de un pool de almacenamiento tipo Directory](modulo4/directory.md)
    * [Añadir nuevos discos a una máquina virtual](modulo4/nuevo_almacenamiento.md)
    * [Gestión de los discos de una máquina virtual](modulo4/gestion_almacenamiento.md)
        * [Actividad 4.1: Creación de un pool de almacenamiento para trabajar con imágenes de discos (OBLIGATORIA)](modulo4/actividad1.md)
        * [Actividad 4.2: Añadir nuevos discos a una máquina virtual (OBLIGATORIA)](modulo4/actividad2.md)
        * Actividad 4.3: ....

5. Clonación, instantáneas y copias de seguridad
    * [Clonación de máquinas virtuales](modulo5/clonacion.md)
    * [Convirtiendo máquinas virtuales en plantillas](modulo5/plantillas.md)
    * [Snapshots de máquinas virtuales](modulo5/snapshot.md)
    * [Copias de seguridad de máquinas virtuales](modulo5/backup.md)
        * [Actividad 5.1: Clonación de máquinas virtuales (OBLIGATORIA)]()
        * [Actividad 5.2: Trabajando con plantillas (OBLIGATORIA)]()
        * [Actividad 5.3: Instantáneas de máquinas virtuales (OBLIGATORIA)]()
        * [Actividad 5.4: Copias de seguridad de máquinas virtuales (OBLIGATORIA)]()
         .......
        * [Actividad 5.2: Creación de un escenario  de trabajo (2ª parte) (VOLUNTARIA)](modulo5/actividad2.md)
        * [Actividad 5.3: Creación de un escenario  de trabajo (3ª parte) (VOLUNTARIA)](modulo5/actividad3.md)

6. Trabajando con Linux Containers
    * [Proxmox y LXC](modulo6/introduccion.md)
    * [Gestionando plantillas de contenedores](modulo6/plantillas.md)
    * [Creación de contenedores Linux](modulo6/contenedor.md)
    * [Gestión de contenedores Linux](modulo6/gestion.md)
    * [Añadir almacenamiento a un contenedor LXC](modulo6/mount.md)
        * Actividad 6.1: Creación de un contenedor LXC (OBLIGATORIA)
        * Actividad 6.2: Añadir almacenamiento a un contenedor LXC (OBLIGATORIA) 
        * Actividad 6.3:

7. Introducción a las redes en Proxmox
    * [Gestionando redes en Proxmox VE](modulo7/introduccion.md)
    * [Configuración de la red del servidor Proxmox VE](modulo7/red_servidor.md)
    * [Configuración de una red interna](modulo7/red_interna.md)
    * [Conexión de una máquina virtual a la red interna](modulo7/conexion_red_intena.md)
    * [Conexión de un un contenedor LXC a la red interna](modulo7/conexion_red_intena2.md)
    * [Introducción al cortafuegos de Proxmox VE](modulo7/cortafuegos.md)
        * Actividad 7.1: Creación de un red interna (OBLIGATORIA)
        * Actividad 7.2: Configuración de un router en Proxmox VE (OBLIGATORIA)
        * Actividad 7.3: Trabajando con el cortafuegos (VOLUNTARIA)

8. Gestión de usuarios en Proxmox VE
    * [Introducción a la gestión de usuarios](modulo8/introduccion.md)
    * [Gestión de Usuarios y Grupos](modulo8/usuarios.md)
    * [Gestión de Pools de Recursos](modulo8/pools.md)
    * [Gestión de Permisos](modulo8/permisos.md)
    * [Ejemplo 1: Especificar tipos de usuarios](modulo8/ejemplo1.md)
    * [Ejemplo 2: Aislamiento de usuarios](modulo8/ejemplo2.md)
        * Actividad 8.1: Gestión de usuarios y grupos (OBLIGATORIA)
        * Actividad 8.2: Trabajando con pools de recursos (OBLIGATORIA)
        * Actividad 8.3: Aislamiento de usuarios (VOLUNTARIA)
