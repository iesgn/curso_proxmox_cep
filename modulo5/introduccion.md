# Gestionando redes en Proxmox VE

Proxmox VE nos ofrece, de una manera muy sencilla, la gestión de las redes con las que va a trabajar. Esta gestión la podemos hacer en dos niveles:

* Podemos configurar **la configuración de red del servidor Proxmox VE** para determinar el tipo de conexión que tendrá el servidor con el exterior.
* Podemos configurar **la configuración de red que tendrán las máquinas virtuales y contenedores** que gestionemos en nuestro servidor Proxmox.

Antes de estudiar detenidamente cada una de estos niveles, vamos a introducir un concepto de redes con el que vamos a trabajar: un **puente o bridge/switch** es un dispositivo de interconexión de redes. En concreto, **Linux Bridge** es un software que tiene la misma funcionalidad que un bridge físico. 

Tenemos más opciones para implementar un bridge por software, pero la más fácil de usar y la que vamos a usar nosotros en Proxmox VE es **Linux Bridge**.



