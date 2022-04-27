# Gestionando plantillas de contenedores

Los contenedores LXC se crean a partir de una **plantilla**. Un plantilla es el sistema de ficheros que va a utilizar el contenedor. Tendremos plantillas para las distintas distribuciones de Linux.

En Proxmox necesitamos descargar las plantillas que vamos a usar para la creación de LXC. Al crear un contenedor se clonara la plantilla para que el contenedor tenga su sistema de fichero. Este proceso se hace de manera muy rápida.

## Descargar plantillas en Proxmox

Como indicamos en unidades anteriores en el pool de lamacenamiento **Local** podemos gaurdar, entre otras cosas, las **plantillas que usaremos para crear los contenedores.

De esta forma, si accedemos al almacienamiento **Local**, y elegimos la opción **CT Templates** accedemos a la ventana que nos permite gestionar las plantillas.

**Imágen de acceso a CT templates**

Tenemos tres formas de obtener plantillas:

* **Upload**: Podemos subir una plantilla que tengamos en nuestro ordenador local.
* **Download from URL**: Podemos descargar una plantilla usando una URL.
* **Templates**: Proxmox nos ofrece un repositorio con un conjunto de plantillas que podemos descargar.

En este curso vamos a usar esta tercera opción. Podemos elegir, por ejemplo, el template de *Ubuntu-22.04-standard* y descargarlo con el botón **Download**.

**Imágen de lista de templates con ubuntu seleccionada**

Además tenemos un buscador que nos permite buscar por nombre:

**Imágen de lista de templates buscando ubuntu**

Una vez descargada podemos comprobar que tenemos la plantilla disponible:

**Imágen de templates descargadas**



