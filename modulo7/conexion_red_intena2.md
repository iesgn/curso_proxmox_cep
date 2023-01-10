# Conexión de un contenedor LXC a la red interna

De forma similar a lo estudiado en el punto anterior, podríamos conectar un contenedor LXC a una red interna.

## Añadir una nueva interfaz de red a un contenedor

Si quisiéramos añadir una nueva interfaz de red a un contenedor LXC, tendríamos que elegir la opción **Network** del contenedor, para ver las interfaces de red que tiene configurado, y pulsar el botón **Add** para añadir una nueva:

![img](img/red19.png)

Podemos nombrar la nueva interfaz de red y el bridge al que se conectará, indicando directamente el direccionamiento estático:

![img](img/red20.png)

## Crear un contenedor conectado a una red interna

En el caso de la creación de un contenedor LXC podemos configurar la interfaz de red conectada al nuevo bridge, indicando directamente el direccionamiento estático:

![img](img/red18.png)

* [Vídeo: Conexión de un contenedor LXC a la red interna](https://youtu.be/5WRbJC_2xH0)
