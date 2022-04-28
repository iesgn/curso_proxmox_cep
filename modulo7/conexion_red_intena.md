# Conexión de una máquina virtual a la red interna

Una vez tenemos nuestro bridge **vmbr1** tenemos dos posibilidades:

* Conectarle una máquina que ya está funcionando. Es decir, añadir una interfaz de red a una máquina ya existente.
* Crear una nueva máquina conectada a este bridge.

Para explicar este apartado vamos a construir el siguiente esquema de red:

![img](img/esquema_red.png)

* La máquina *router* ya está creada y está conectada al bridge **vmbr0**, le vamos a añadir una interfaz conectada la bridge **vmbr1** y lo vamos a configurar con la ip `10.0.0.1`.
* La máquina *cliente* la vamos a crear conectada al bridge **vmbr1** con la dirección `10.0.0.2`.

## Añadir una nueva interfaz de red a una máquina

La máquina *router* ya está funcionando y tiene una interfaz de red conectada a **vmbr0**. Podemos añadirle una nueva interfaz de red desde el apartado **Hardware** de la máquina:

![img](img/red9.png)

Elegimos al bridge al que va a estar conectada esta nueva interfaz (recuerda elegir el driver VirtIO):

![img](img/red10.png)

En la red interna a la que hemos conectado la red no existe ningún servidor DHCP por lo que tendremos que hacer una configuración manual del direccionamiento de esta interfaz. La manera de hacer esta configuración dependerá del sistema operativo de la máquina que estamos configurando (nn mi caso es una distribución Debian). Podemos comprobar que ya tenemos dos interfaces configuradas:

![img](img/red11.png)

La nueva interfaz se llama `ens19` y es la que tenemos que configurar para ello modificamos el fichero `/etc/network/interfaces` y añadimos el siguiente contenido:

![img](img/red12.png)

Y para terminar la configuración levantamos la interfaz con `ifup` y comprobamos que ya hemos configurado la ip:

![img](img/red13.png)

## Crear una nueva máquina virtual conectada a la red interna

La máquina *cliente* la vamos a crear conectada directamente al nuevo bridge. Para ello durante la configuración de la nueva máquina escogemos el nuevo bridge:

![img](img/red14.png)

Una vez creada, comprobamos que esta maquina está conectada a **vmbr1**:

![img](img/red15.png)

De la misma forma que hemos configurado la ip en la máquina *router*, vamos a configurar la ip a esta máquina. Vamos a configurar la ip `10.0.0.2`:

![img](img/red16.png)

Y comprobamos que hay conectividad con la otra máquina:

![img](img/red17.png)

## Conclusiones

La creación de diferentes Linux Bridge nos posibilita la construcción de escenarios complejos de red. Además tenemos que tener en cuenta que añadir o eliminar una interfaz se puede hacer en "caliente" sobre una máquina que este funcionando. Del mismo modo podemos modificar una interfaz de red ya existente para modificar el bridge al que está conectada.