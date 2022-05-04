# ACTIVIDAD Nº 3

## TÍTULO DE LA ACTIVIDAD: Configuración de un router

## TEXTO DE LA ACTIVIDAD

En esta actividad vamos a terminar de configurar el escenario con el que estamos trabajando en este módulo. **Puedes deshabilitar el cortafuegos de la actividad anterior para que no tengas ningún tipo de problema**. Vamos a configurar un router/nat en la máquina virtual `router` para que el contenedor `cliente` tenga acceso a internet:

Si ejecutamos un `ip r` en el `cliente` vemos que la ruta por defecto manda los paquetes a la máquina `router`. Pero tenemos que configurar esa máquina para que enrute los paquetes que proveniente del `cliente`, además debemos configurar SNAT para que el `cliente` tenga acceso al exterior. Para ello en la máquina `router`:

1. Activamos el bit de forwarding. Modificamos el fichero `/etc/sysctl.conf` y descomentamos la línea `net.ipv4.ip_forward=1`. Para confirmar el cambio ejecutamos `sysctl -p`.
2. Añadimos una regla en el cortafuego para realizar el SNAT. Para ello instalamos `iptables`:

    ```
    # apt install iptables
    ```

    Y añadimos en el fichero `/etc/network/interface` la regla:

    ```
    post-up iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o ens18 -j MASQUERADE
    ```
    Es decir los paquetes que vengan de la red interna 10.0.0.0/24, y saliendo por la primera interfaz se enmascaran, es decir su dirección de origen se cambian por la dirección de la interfaz de salida. Por último reiniciamos la red para activar la configuración. 

    **Nota: Cambia el nombre de la interfaz de red o cualquier otro datos si en tu escenario es necesario.**

3. Para ejecutar la regla iptable podemos reiniciar la segunda interfaz de red:

```
# ifdown ens19
# ifup ens19
```

Y podemos comprobar que la regla se ha ejecutado:

```
# iptables -L -n -t nat
...

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  10.0.0.0/24          0.0.0.0/0 
```

Ahora podemos comprobar que el `cliente` tiene acceso al exterior:

    ```
    cliente:~$ ping 1.1.1.1
    PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
    64 bytes from 1.1.1.1: icmp_seq=1 ttl=56 time=9.05 ms
    ```

Para superar la actividad deberás entregar en un fichero comprimido los siguientes pantallazos:

1. Un pantallazo donde se vea la ejecución del comando `ip a` en la máquina `router`.
2. Un pantallazo donde se vea la ejecución del comando `ip a` en la máquina `cliente`.
3. Un pantallazo donde se vea la ejecución del comando `ip r` en la máquina `cliente`.
4. Un pantallazo donde se vea la ejecución del comando `ping 1.1.1.1` en la máquina `cliente`.

## RECURSOS

* Conexión a Internet

## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

No

## ¿ES UNA ACTIVIDAD INDIVIDUAL O DE GRUPO?

Individual

## ¿ES UNA ACTIVIDAD CALIFICABLE?

Sí

### ¿Tiene que ser calificada por el tutor/a? (S/N)

Sí

### ¿Es de calificación automática?

No

### ¿Es calificada por el resto de compañeros/as del curso? (S/N)

No

## EVALUACIÓN

* Se entregan los documentos, contienen lo solicitado y los contenidos son originales.

## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

No

## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

1 hora
