# Dispositivos paravirtualizados

Al crear las máquinas virtuales, además de las características básicas
como la cantidad de RAM asignada, el espacio de almacenamiento o la
CPU, se deben seleccionar los diferentes dispositivos que van a formar
parte de ella: interfaz de red, controladores de disco duro, interfaz
gráfica, etc. En un sistema de virtualización completa como QEMU/KVM
todos los dispositivos están inicialmente emulados por software, de
manera que la máquina virtual interactúa con un dispositivo como si lo
hiciera con uno físico equivalente. De esta manera podemos encontrar
una interfaz de red emulando a la clásica tarjeta de red Realtek 8139
o una interfaz IDE para conectar con un disco duro virtual. Estos
dispositivos emulados tienen la ventaja de que pueden utilizar los
controladores de dispositivos de sus equivalentes físicos, por lo que
se suelen utilizar dispositivos emulados muy comunes, que proporcionan
compatibilidad con la mayoría de sistemas operativos y hacen muy
sencilla la instalación de los mismos dentro de una máquina
virtual. Sin embargo, tienen un inconveniente y es que cuando son
dispositivos muy usados, tienen un rendimiento pobre, aumentan el
consumo de recursos de la CPU y aumentan la latencia de E/S.

El proyecto KVM proporciona una alternativa al uso de dispositivos
emulados, que se conocen como dispositivos paravirtualizados y se
engloban bajo la denominación
[virtIO](https://www.linux-kvm.org/page/Virtio). El nombre de
dispositivos paravirtualizados hace referencia a la técnica que
utilizan, más cercana a la paravirtualización y que proporciona un
rendimiento muy cercano al real, por lo que es muy recomendable
utilizar dispositivos virtio en los dispositivos de E/S que consumen
más recursos, por ejemplo, la red y el acceso a discos duros.
El único inconveniente que tiene utilizar dispositivos virtio es que
son específicos para KVM y no todos los sistemas operativos los
reconocen por defecto. Evidentemente los sistemas linux sí reconocen
los dispositivos virtio y en ese caso siempre es recomendable usarlos,
pero otros sistemas operativos, como por ejemplo Windows, no incluyen
inicialmente soporte virtio, si queremos usarlos en ese caso, será
necesario instalar los controladores de dispositivos durante la
instalación del sistema operativo de la máquina virtual.
