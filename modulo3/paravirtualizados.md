# Dispositivos paravirtualizados

Al crear las máquina virtuales vamos a seleccionar los dispositivos que formaran parte de ella. Gran parte de los dispositivos están emulados (placa base, algunos controladores de red, controladores de disco duros IDE, SATA, SCSI, puerto serie,...), por lo que el rendimiento es menor.

Todos estos dispositivos se emulan con la ejecución de un  software cuyo comportamiento es equivalente a los dispositivos de hardware, y si el sistema operativo que se ejecuta en la máquina virtual tiene los controladores adecuados, utilizará los dispositivos como si se ejecutara en hardware real. Esto permite que Qemu ejecute sistemas operativos no modificados. 

Sin embargo, esto tiene un costo de rendimiento, ya que ejecutar en software lo que estaba destinado a ejecutarse en hardware implica mucho trabajo adicional para la CPU del host.

Para mitigar esto, Qemu puede presentar al sistema operativo invitado dispositivos paravirtualizados, con lo que aumentamos el rendimiento.

Cuando escojamos la interfaz de comunicación de los discos duros y de las tarjetas de red de nuestra máquina virtual vamos a seleccionar controladores VirtIO. Estos dispositivos son paravirtualizados por KVM (no emulados) y por lo tanto nos ofrecen mayor rendimiento (consulte [http://www.linux-kvm.org/page/Virtio](http://www.linux-kvm.org/page/Virtio)).