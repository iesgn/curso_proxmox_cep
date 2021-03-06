# Proxmox y LXC

Además de las máquinas virtuales, en Proxmox tenemos la posibilidad de crear y gestionar contenedores: **Linux Containers (LXC)**.

Los contenedores son una alternativa ligera a las máquinas totalmente virtualizadas. Utilizan el núcleo del sistema anfitrión en el que se ejecutan, en lugar de emular un sistema operativo completo. 

Como ventaja, podemos indicar que los recursos para la ejecución de LXC son bajos. Pero tenemos también la limitación de que sólo podemos crear contenedores con distribuciones Linux. No es posible ejecutar otros sistemas operativos como, por ejemplo, FreeBSD o Microsoft Windows dentro de un contenedor.

En esta unidad vamos a aprender a trabajar con LXC en Proxmox.

---

Para seguir profundizando:

* [Proxmox Container Toolkit](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#chapter_pct)