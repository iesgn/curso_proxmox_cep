# Tipos de virtualización

En el punto anterior aprendimos que un **Hipervisor** es el software que nos permite realizar la virtualización. Según como funcione el Hypervisor podemos clasificar distintas técnicas de virtualización:

## Emulación

El hipervisor imita o suplanta vía software una arquitectura al completo (procesador, memoria, conjunto de instrucciones, comunicaciones...). De esta forma puede hacer creer a los programas y sistemas operativos diseñados para una arquitectura concreta que son ejecutados sobre ella. La emulación suele ofrecer un rendimiento bastante bajo debido a que hay que realizar un proceso completo de traducción. Ejemplo: QEMU, Microsoft Virtual PC, Wine, ...

## Virtualización completa o por hardware

El hipervisor simula un hardware suficiente para permitir que un sistema operativo no adaptado se ejecute de forma aislada. En este caso podemos hacer una subdivisión según el tipo de hypervisor que estemos utilizando:

### Virtualización por hardware

En este caso usamos hipervisores de tipo 1, que controlan directamente el hardware físico del host ofreciéndolo directamente a la máquina virtual. Es imprescindible que la CPU del host tenga las extensiones de virtualización. Ejemplos: Xen, Kernel-based Virtual Machine (KVM), Microsoft Hyper-V, VMware ESXi,...

### Virtualización completa

En este tipo se usan hipervisores de tipo 2. Este software se intala sobre el sistema oprativo del host, pero no controla directamente el hardware físico. Ofrecen menos rendimiento que la virtualización por hardware. Ejemplos: VMware Workstation, Parallels Desktop, VirtualBox, VMware Player, ...

## Virtualización parcial o paravirtualización

El hipervisor ofrece un interfaz especial para acceder a los recursos. En ocasiones, es necesario la adaptación del sistema operativo de la máquina virtual. Ofrecen el máximo rendimiento, pero no se pueden usar sistemas operativos sin modificaciones o hardware especifico. Ejemplos: XEN, Microsoft Hyper-V, VMware ESXi, ...

## Virtualización ligera

