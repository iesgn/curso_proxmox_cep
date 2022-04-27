# Introducción a Proxmox VE

**Proxmox Virtual Environment**, o **Proxmox VE** es un entorno de virtualización de servidores de código abierto. Es una distribución de GNU/Linux basada en Debian que permite el despliegue y la gestión de máquinas virtuales y contenedores.

## Virtualización con Proxmox VE

La versión actual de Proxmox VE nos permite gestionar los siguientes recursos virtualizados:

* **Máquinas virtuales**: Para ello utiliza **virtualización por hardware** con el uso del hipervisor KVM.
* **Contenedores**: Podemos gestionar **contenedores de sistema** LXC.

## Otras características

* Ofrece una consola web para la gestión de los recursos virtualizados.
* Ofrece herramientas de línea de comandos para la gestión de los recursos virtualizados.
* Ofrece una API REST que nos permite la gestión de los recursos virtualizados desde un programa diseñado por nosotros.
* Permite la creación de un clúster de servidores Proxmox.
* si tenemos configurado un clúster de servidores Proxmox tendremos características de alta disponibilidad y de migraciones en vivo.
* Permite el uso de muchos tipos de medios de almacenamiento.
* Permite la configuración de la red que van a utilizar las máquinas virtuales y los contenedores.
* Es un programa de código abierto.
* Hay una gran comunidad de soporte y ayuda.
* ...

## Proxmox VE en un centro educativo

Un sistema de virtualización como Proxmox VE puede ser muy adecuado para la enseñanzas de las TIC en nuestros centros educativos.

Por un lado nos beneficiamos de todas las características que estudiamos sobre la virtualización y por otro lado podemos hacer que los recursos virtualizados que usan los alumnos no se estén ejecutando en su máquina física.

Si una máquina física de un alumno se estropea podrá seguir usando los recursos virtualizados sin problemas, porque se están ejecutando en un servidor o en un clúster de servidores.