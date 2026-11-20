# Propuesta de actividades para la versión Proxmox VE 9

> **Documento de trabajo.** No modifica ninguna actividad. Sirve para decidir cómo
> quedarán los ejercicios de esta versión y, una vez aprobado, aplicar los cambios
> en los ficheros `moduloN/actividadN.md` y en el `README.md`.
>
> Fecha: 20/11/2026. Estado: **pendiente de aprobación del autor**.

## Decisiones tomadas

- **1.1:** se mantiene igual.
- **2.1:** se mantiene; cambia el tiempo a **2 h** (como figura en el `README.md`)
  y el paso 2, que pasa a explicar las dos alternativas de instalación (máquina
  física o máquina virtual con VirtualBox).
- **Módulo 3:** se fusiona en una sola actividad, «Creación de máquinas virtuales»,
  con **2 h**. La 3.1 se mantiene y absorbe la 3.3; la 3.2 pasa a «Parte optativa
  (No hay que entregar nada)»; la 3.4 se elimina.
- **Módulo 4:** se fusionan la 4.1 y la 4.2 en una sola actividad, «Gestión del
  almacenamiento con Proxmox», de **2 h**; la parte voluntaria (sin entrega)
  redimensiona y mueve el disco de la parte obligatoria y, al final, crea una VM
  nueva con su disco en `imagenes-discos`.
- **Módulo 5:** se fusiona en una sola actividad, «Clonación, plantillas,
  instantáneas y copias de seguridad», con **2 h**. La parte obligatoria une 5.1 +
  5.2; la parte voluntaria (sin entrega) une 5.3 + 5.4.
- **Módulo 6:** se fusiona en una sola actividad, «Creación y almacenamiento de un
  contenedor LXC», con **2 h**; la 6.2 se integra en la 6.1.
- **Módulo 7:** se fusiona en una sola actividad, «Configuración de una red interna
  y del cortafuegos», con **2 h**. La parte obligatoria une 7.1 + 7.2; la parte
  voluntaria (sin entrega) recoge 7.3.
- **Módulo 8:** la 8.1 se mantiene con **2 h** y se le añade el permiso
  `PVESDNUser` en el Ejemplo 2 (y una nota para los operadores del Ejemplo 1).

## Criterios utilizados

- **Proxmox VE 9.2** (Debian 13 Trixie), comprobado en la VM `pve9-curso`.
- **Laboratorio del curso:** Proxmox anidado en VirtualBox, 8 GB de RAM, 100 GB de
  disco y 4 núcleos. Hay que evitar actividades que obliguen a tener varias VM
  grandes encendidas a la vez.
- **Agenda del `README.md`:** las horas de las actividades deben cuadrar con ella.
- **Windows:** Windows 10 ya no tiene soporte. Windows 11 exige UEFI, TPM 2.0,
  Secure Boot y 4 GB de RAM, y ocupa 64 GiB de disco. En un Proxmox anidado con
  8 GB es posible, pero lento y justo de espacio.
- **Formato:** se mantienen las 8 secciones y los nombres de los ficheros. Solo se
  actualiza el texto de las actividades y su estado (obligatoria/voluntaria).
- **eXeLearning:** las actividades no están en los `.elp`, así que estos cambios no
  obligan a regenerar los paquetes de eXeLearning.

## Resumen de la propuesta

| Actividad | Estado actual | Propuesta | Motivo |
| --- | --- | --- | --- |
| 1.1 Foro de experiencia previa | Obligatoria, 30 min | **Mantener** | Sigue teniendo sentido y ya está actualizada. |
| 2.1 Instalación y acceso | Obligatoria, 1 h | **Mantener**; tiempo a 2 h y nuevo paso 2 | Se explican las dos vías de instalación: máquina física (recomendada) o máquina virtual con VirtualBox (anidada). |
| 3.1–3.4 (módulo 3) | 3.1 y 3.2 obligatorias; 3.3 y 3.4 voluntarias | **Fusionar en una sola actividad 3.1** «Creación de máquinas virtuales» (2 h): 3.1 + 3.3; 3.2 a «Parte optativa (No hay que entregar nada)»; 3.4 se elimina | Simplifica el módulo, mantiene Linux como obligatorio y saca Windows de la parte evaluable. |
| 4.1–4.3 (módulo 4) | 4.1 y 4.2 obligatorias; 4.3 voluntaria | **Fusionar 4.1 + 4.2 en una sola actividad** «Gestión del almacenamiento con Proxmox» (2 h); parte voluntaria sin entrega: gestión del disco de la parte obligatoria + VM nueva con disco en el pool | Simplifica el módulo y mantiene la creación de discos en el pool y la gestión de discos como ampliación opcional. |
| 5.1–5.4 (módulo 5) | 5.1 y 5.2 obligatorias; 5.3 y 5.4 voluntarias | **Fusionar en una sola actividad** «Clonación, plantillas, instantáneas y copias de seguridad» (2 h): obligatorio 5.1 + 5.2; voluntario (sin entrega) 5.3 + 5.4 | Simplifica el módulo y deja las instantáneas y copias como ampliación opcional. |
| 6.1–6.2 (módulo 6) | 6.1 y 6.2 obligatorias | **Fusionar en una sola actividad** «Creación y almacenamiento de un contenedor LXC» (2 h) | Simplifica el módulo y mantiene la creación y el almacenamiento en un mismo flujo. |
| 7.1–7.3 (módulo 7) | 7.1 y 7.2 obligatorias; 7.3 voluntaria | **Fusionar en una sola actividad** «Configuración de una red interna y del cortafuegos» (2 h): obligatorio 7.1 + 7.2; voluntario (sin entrega) 7.3 | Simplifica el módulo y deja el router/NAT como ampliación opcional. |
| 8.1 Gestión de usuarios | Obligatoria, 1 h | **Mantener** y corregir a 2 h | Añadir el rol `PVESDNUser`; sin él, el Ejemplo 2 no puede crear VM. |

**No se propone eliminar ninguna actividad.** Las voluntarias conservan contenido
útil y no alargan la parte obligatoria.

---

## Detalle por módulo

### Módulo 1

#### Actividad 1.1 — Foro de experiencia previa

- **Se mantiene obligatoria** y con 30 minutos.
- No requiere cambios de contenido: ya se actualizó la pregunta 4 y el tiempo.
- Sin dependencias.

### Módulo 2

#### Actividad 2.1 — Instalación y acceso a Proxmox VE

- **Se mantiene obligatoria.** Se mantienen el título, el paso 1, el paso 3 y los
  pantallazos.
- **Tiempo:** 1 h → **2 h**, el valor que figura en el `README.md`.
- **Paso 2:** se sustituye por una lista con las dos alternativas de instalación.

  Texto propuesto:

  ```markdown
  2. Elige una de estas dos alternativas para instalar Proxmox VE:

     * **La más deseable, si es posible:** instalar Proxmox VE en una **máquina
       física** con recursos suficientes. Así evitas la virtualización anidada y
       tendrás mucho más rendimiento.
     * **La segunda opción:** usar un sistema de virtualización (en el curso hemos
       explicado **VirtualBox**) y crear una máquina virtual con las
       características recomendadas que hemos visto en el contenido del tema. En
       este caso usarás virtualización anidada y tendrás menos rendimiento; por
       ejemplo, la instalación de una máquina virtual con Windows puede darte
       muchos problemas.
  ```

- No se añaden más requisitos: el resto de la actividad remite al contenido del
  módulo para la instalación y el acceso.
- Dependencias: ninguna.

### Módulo 3

> **Decisión (20/11/2026):** el módulo 3 queda reducido a **una sola actividad**
> obligatoria. La 3.3 se integra en la 3.1, la 3.2 (Windows) pasa a una sección
> optativa sin entrega y la 3.4 se elimina.

#### Actividad 3.1 — Creación de máquinas virtuales

- **Cambia el título:** «Creación de una máquina virtual Linux» → «Creación de
  máquinas virtuales».
- **Tiempo:** 1 h → **2 h** (decidido por el autor el 20/11/2026).
- **Cambios en los pasos de la 3.1:**
  - Se mantienen los pasos 1 y 2 (ISO y creación de la VM, con 512 MiB).
  - Se elimina el paso 3 (arranque automático).
  - Se mantiene el paso 4 (acceso por consola), que pasa a ser el 3.
  - Se elimina el paso 5 (instalar SSH).
  - Se integra la 3.3 en un único paso: instalar (si es necesario) el
    `qemu-guest-agent` y activar **Options → QEMU Guest Agent**.
  - Se elimina el paso de mostrar la IP.
- **Pantallazos:** se quedan en tres:
  1. *Hardware* de la VM.
  2. Acceso por consola.
  3. Dirección IP configurada.
- **Texto propuesto para la parte obligatoria:**

  ```markdown
  En esta actividad vamos a crear nuestra primera máquina virtual. Para ello:

  1. Sube una imagen ISO de tu distribución preferida de Linux.
  2. Crea una nueva máquina virtual en Proxmox, e instala el sistema operativo a
     partir de la imagen ISO que has subido anteriormente. Al configurar los
     recursos de la máquina ten en cuenta los recursos que tiene tu host, para una
     máquina linux sin entorno gráfico serían suficientes 512 MiB de RAM.
  3. Una vez instalada la máquina accede a ella desde una consola de Proxmox VE.
  4. Instala (si es necesario) el programa Qemu-guest-agent en la máquina virtual
     que has creado. En Debian 13 el agente ya se instala con el sistema; en ese
     caso solo tienes que configurar la máquina para que utilice la comunicación
     con el agente. Recuerda que debes activar la opción **QEMU Guest Agent** en
     el apartado **Options** de la máquina.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  1. Un pantallazo donde se vea el apartado **Hardware** de la máquina que has
     creado.
  2. Un pantallazo donde se vea el acceso a la máquina virtual una vez instalada
     usando la consola de Proxmox VE.
  3. Un pantallazo donde se vea la dirección IP configurada en la máquina.
  ```

- Dependencias: ninguna.

#### Parte optativa de la actividad 3.1

- Se añade al final del texto de la actividad una sección titulada **«Parte
  optativa (No hay que entregar nada)»**, con el contenido actualizado de la
  **3.2 (Windows)**.
- No se entrega nada: no hay pantallazos ni documento.
- Texto propuesto:

  ```markdown
  ## Parte optativa (No hay que entregar nada)

  Si quieres practicar también con Windows, puedes crear una máquina virtual con
  el sistema operativo Windows. Para ello:

  1. Sube una imagen ISO de **Windows 11 Pro**.
     * **Nota 1**: Asegúrate de instalar la versión Pro para tener posibilidad de
       acceso remoto (la edición Home no lo permite).
     * **Nota 2**: Windows 11 exige UEFI, TPM 2.0 y Secure Boot, y al menos 4 GiB
       de RAM y 64 GiB de disco. En un Proxmox anidado con 8 GB de RAM y 100 GB de
       disco puede ser lento y ocupar mucho espacio; si no dispones de recursos
       suficientes, puedes omitir esta parte.
  2. Sube la imagen ISO de los drivers VirtIO.
  3. Crea una nueva máquina virtual en Proxmox con la configuración que hemos
     indicado en el contenido del módulo: q35, OVMF (UEFI), disco EFI, TPM v2.0,
     4 GiB de RAM y un disco de 64 GiB. No olvides elegir VirtIO SCSI para el
     disco y VirtIO para la interfaz de red.
  4. Marca la casilla **Add additional drive for VirtIO drivers** para añadir un
     CDROM con los drivers VirtIO y configura la máquina para que arranque de
     forma adecuada con el instalador de Windows.
  5. Instala de forma adecuada los drivers VirtIO para detectar el disco duro
     durante la instalación: carga el controlador `vioscsi\w11\amd64` desde el CD
     de VirtIO y termina la instalación de la máquina.
  6. Una vez instalada la máquina, accede a ella desde un terminal de Proxmox VE.
     En la configuración inicial sin red, crea una cuenta local con
     `start ms-cxh:localonly`.
  7. Instala `virtio-win-guest-tools.exe` desde el CD de VirtIO para configurar de
     forma adecuada los drivers de la tarjeta de red y tener acceso a internet.
  8. Configura el acceso remoto y accede a la máquina usando un cliente RDP
     (Remmina o Conexión a Escritorio remoto).
  ```

- Motivos: Windows 10 está fuera de soporte; Windows 11 es pesado para el
  laboratorio y no debe condicionar la actividad obligatoria. Al no tener entrega,
  el alumno puede omitirlo sin afectar a la superación del curso.
- **Se elimina la actividad 3.4** (instalación de servicios) y su fichero.
- **Ficheros:** al quedar una sola actividad, se eliminan `actividad2.md`,
  `actividad3.md` y `actividad4.md`; todo el contenido queda en `actividad1.md`.

### Módulo 4

> **Decisión (20/11/2026):** el módulo 4 queda reducido a **una sola actividad**
> obligatoria que une la 4.1 y la 4.2. La 4.3 pasa a una **parte voluntaria**
> dentro de esa actividad.

#### Actividad 4.1 — Gestión del almacenamiento con Proxmox

- **Cambia el título:** «Creación de una fuente de almacenamiento para trabajar
  con imágenes de discos» → «Gestión del almacenamiento con Proxmox».
- **Tiempo:** 1 h + 1 h → **2 h** (suma de las dos actividades de la agenda).
- **Se unen la 4.1 y la 4.2** en un único texto:
  - Fuente Directory `imagenes-discos` en `/var/lib/imagenes`, con contenidos
    **Disk image** y **Container**.
  - Nuevo disco de **1 GiB** en `imagenes-discos` para una VM ya creada,
    formateado y montado en `/mnt`.
- **Pantallazos:** características de la fuente, *Hardware* con el disco nuevo y
  disco montado en `/mnt` (tres en total).
- **Parte voluntaria:** se añade al final la gestión del disco de la 4.3
  (redimensionar el disco de la parte obligatoria y moverlo a `local-lvm`) y la
  creación de una **VM nueva con su disco en `imagenes-discos`**, **sin entrega**.
  No es necesaria para superar la actividad.
- **Texto propuesto:**

  ```markdown
  # ACTIVIDAD Nº 1

  ## TÍTULO DE LA ACTIVIDAD: Gestión del almacenamiento con Proxmox

  ## TEXTO DE LA ACTIVIDAD

  En esta actividad vamos a crear una fuente de almacenamiento de tipo Directory
  para trabajar con imágenes de discos y vamos a añadir un nuevo disco a una
  máquina virtual. Para ello necesitas tener una máquina virtual ya creada, a la
  que añadirás el disco. Sigue los siguientes pasos:

  1. Crea una nueva fuente de almacenamiento de tipo Directory. El directorio que
     se va a utilizar será `/var/lib/imagenes` y el nombre será `imagenes-discos`.
     En esta fuente de almacenamiento se podrán guardar imágenes de discos y
     sistemas de archivo de contenedores.
  2. Añade un nuevo disco a la máquina virtual de tamaño 1 GiB, creado en la fuente
     de almacenamiento `imagenes-discos` como un fichero QCOW2.
  3. Accede a la máquina virtual, formatea el disco y móntalo en `/mnt` como se ha
     mostrado en el contenido del módulo.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  1. Un pantallazo de las características de la fuente de almacenamiento creada.
     La pantalla que aparece con la opción **Edit** del almacenamiento creado
     (`Datacenter->Storage->imagenes-discos`).
  2. Un pantallazo donde se vea el apartado **Hardware** de la máquina para
     comprobar que hemos añadido un nuevo disco de 1 GiB guardado en el
     almacenamiento `imagenes-discos`.
  3. Un pantallazo donde se vea que el disco está montado en `/mnt`.

  ## Parte voluntaria (No hay que entregar nada)

  En esta parte vamos a trabajar con el disco que hemos creado en la parte
  obligatoria y también vamos a crear una nueva máquina virtual cuyo disco se
  guarde en la fuente de almacenamiento `imagenes-discos`. Esta parte es
  voluntaria y no hay que entregar nada:

  1. Redimensiona el disco que hemos creado en la parte obligatoria a 2 GiB.
  2. Accede a la máquina y redimensiona el sistema de ficheros como se ha mostrado
     en el contenido del módulo.
  3. Mueve el contenido del disco al almacenamiento `local-lvm`.
  4. Cuando creas una nueva máquina virtual puedes elegir la fuente de
     almacenamiento donde se crea su disco: crea una nueva máquina virtual Linux y
     elige `imagenes-discos` como almacenamiento de su disco, en formato QCOW2.

  ## RECURSOS

  * Conexión a Internet

  ## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

  Sí

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

  * Se entregan los documentos, contienen lo solicitado y los contenidos son
    originales.

  ## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

  No

  ## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

  2 horas
  ```

- **Ficheros:** `actividad1.md` queda con todo; se eliminan `actividad2.md` y
  `actividad3.md`.

### Módulo 5

> **Decisión (20/11/2026):** el módulo 5 queda reducido a **una sola actividad**
> obligatoria. La parte obligatoria une la 5.1 (clonación) y la 5.2 (plantillas);
> la parte voluntaria (sin entrega) une la 5.3 (snapshots) y la 5.4 (copias de
> seguridad).

#### Actividad 5.1 — Clonación, plantillas, instantáneas y copias de seguridad

- **Cambia el título:** «Clonación de máquinas virtuales» → «Clonación, plantillas,
  instantáneas y copias de seguridad».
- **Tiempo:** 1 h + 1 h → **2 h** (suma de la 5.1 y la 5.2 de la agenda).
- **Parte obligatoria:** une la 5.1 y la 5.2, con nombres fijos:
  - `vm-base`: la VM original que se clona y se convierte en plantilla.
  - `clon-completo`: el clon completo de `vm-base`.
  - `clon-ligero`: el clon ligero creado a partir de la plantilla.
- **Recomendaciones de la 9:**
  - Usar la VM Debian 13, no la de Windows, para no consumir 64 GiB.
  - Clonar con la VM **apagada**: en caliente, `local-lvm` copia el tamaño completo
    y puede llenar el thin pool.
  - En el diálogo *Clone* de una VM normal no aparece *Mode* (siempre es clonación
    completa); *Mode* solo aparece al clonar una plantilla.
  - La clonación ligera necesita qcow2 en un directorio o LVM-thin (`local-lvm`).
- **Parte voluntaria (No hay que entregar nada):** une la 5.3 y la 5.4:
  - Crear un fichero, tomar un snapshot, modificarlo y restaurar.
  - Crear una copia de seguridad, listarla y crear una VM a partir de ella.
  - Recomendaciones: *Include RAM* si la VM está encendida; en *Backup now*,
    Storage `local`, Mode Snapshot, Compression ZSTD; restaurar con un VM ID nuevo.
- **Texto propuesto:**

  ```markdown
  # ACTIVIDAD Nº 1

  ## TÍTULO DE LA ACTIVIDAD: Clonación, plantillas, instantáneas y copias de seguridad

  ## TEXTO DE LA ACTIVIDAD

  En esta actividad vamos a clonar una máquina virtual, convertirla en plantilla y
  crear una nueva máquina a partir de ella. Para que las capturas sean más
  sencillas de revisar, vamos a usar nombres fijos:

  - `vm-base`: la máquina virtual que vamos a clonar y que después convertiremos
    en plantilla.
  - `clon-completo`: el clon completo de `vm-base`.
  - `clon-ligero`: el clon ligero creado a partir de la plantilla.

  Para ello:

  1. Prepara una máquina virtual llamada `vm-base` (puedes usar una que ya tengas
     y renombrarla).
  2. Realiza una clonación completa de `vm-base` para crear `clon-completo`.
  3. Convierte `vm-base` en una plantilla.
  4. A partir de la plantilla `vm-base`, crea una nueva máquina llamada
     `clon-ligero` utilizando la clonación ligera.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  1. Un pantallazo de la parte inicial del log de la tarea de clonación completa,
     donde se vea `create full clone of drive ...`.
  2. Un pantallazo del apartado **Hardware** de `vm-base` mostrando el disco como
     `base-...`, o del menú contextual de la plantilla (donde no aparece *Start*).
  3. Un pantallazo de la parte inicial del log de la tarea de clonación ligera,
     donde se vea `create linked clone of drive ... (base-...)`.
  4. Un pantallazo del árbol de recursos donde se vean `vm-base` (con el icono de
     plantilla), `clon-completo` y `clon-ligero`.

  **Nota:** los logs de las tareas se pueden volver a abrir desde el panel
  **Tasks** de la parte inferior: doble clic sobre la tarea o **Task History** para
  buscarla. No hace falta hacer el pantallazo en el momento.

  ## Parte voluntaria (No hay que entregar nada)

  En esta parte vamos a trabajar con instantáneas y copias de seguridad. Esta parte
  es voluntaria y no hay que entregar nada:

  1. Crea un fichero de texto en una máquina con cualquier información.
  2. Crea un snapshot de la máquina.
  3. Modifica el contenido del fichero creado.
  4. Restaura el estado de la máquina con el snapshot creado.
  5. Crea una copia de seguridad de una máquina.
  6. Muestra la lista de copias de seguridad realizadas.
  7. Crea una nueva máquina a partir de la copia de seguridad realizada.

  ## RECURSOS

  * Conexión a Internet

  ## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

  Sí

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

  * Se entregan los documentos, contienen lo solicitado y los contenidos son
    originales.

  ## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

  No

  ## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

  2 horas
  ```

- **Ficheros:** `actividad1.md` queda con todo; se eliminan `actividad2.md`,
  `actividad3.md` y `actividad4.md`.

### Módulo 6

> **Decisión (20/11/2026):** el módulo 6 queda reducido a **una sola actividad**
> obligatoria que une la 6.1 (creación) y la 6.2 (almacenamiento).

#### Actividad 6.1 — Creación y almacenamiento de un contenedor LXC

- **Cambia el título:** «Creación de un contenedor LXC» → «Creación y
  almacenamiento de un contenedor LXC».
- **Tiempo:** 1 h + 1 h → **2 h** (suma de las dos actividades de la agenda).
- **Se unen la 6.1 y la 6.2** en un único texto:
  - Descargar una plantilla (Debian 13 standard, amd64).
  - Crear el contenedor (Unprivileged + Nesting, `local-lvm`, 8 GiB, DHCP).
  - Acceder por consola.
  - Añadir un Mount Point de 2 GiB en `/srv`.
- **Recomendaciones de la 9:**
  - **CT Templates → Templates**: `debian-13-standard` aparece dos veces (amd64 y
    arm64); elegir **amd64**.
  - *Disks*: elegir **`local-lvm`**, no el almacenamiento que propone por defecto.
  - *Network*: IPv4 es **Static** por defecto; seleccionar **DHCP**.
  - *Confirm*: dejar marcado **Start after created**.
  - **Resources → Add → Mount Point**: ID `mp0`, Storage `local-lvm`, Disk size
    **2 GiB**, Path `/srv`, Backup marcado.
- **Pantallazos:** *Resources* (con el rootfs y el punto de montaje), *Networks*,
  consola con el login y consola con el punto de montaje (`df -h` o
  `mount | grep /srv`).
- **Texto propuesto:**

  ```markdown
  # ACTIVIDAD Nº 1

  ## TÍTULO DE LA ACTIVIDAD: Creación y almacenamiento de un contenedor LXC

  ## TEXTO DE LA ACTIVIDAD

  En esta actividad vamos a crear un contenedor LXC y añadirle un volumen de
  almacenamiento. Para ello:

  1. Descarga una plantilla de tu distribución preferida de Linux.
  2. Crea un nuevo contenedor LXC en Proxmox a partir de la plantilla descargada.
  3. Configura la interfaz de red por DHCP.
  4. Una vez creado el contenedor, accede desde una consola de Proxmox VE.
  5. Añade un volumen de 2 GiB como punto de montaje en el contenedor, en el
     directorio `/srv`.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  1. Un pantallazo del apartado **Resources** del contenedor, donde se vean el
     rootfs y el punto de montaje.
  2. Un pantallazo del apartado **Networks** del contenedor que has creado.
  3. Un pantallazo del acceso al contenedor una vez creado y con el login hecho,
     usando la consola de Proxmox VE.
  4. Un pantallazo donde se vea el punto de montaje en el contenedor, como se
     muestra en el contenido del módulo.

  ## RECURSOS

  * Conexión a Internet

  ## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

  Sí

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

  * Se entregan los documentos, contienen lo solicitado y los contenidos son
    originales.

  ## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

  No

  ## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

  2 horas
  ```

- **Ficheros:** `actividad1.md` queda con todo; se elimina `actividad2.md`.

### Módulo 7

> **Decisión (20/11/2026):** el módulo 7 queda reducido a **una sola actividad**
> obligatoria. La parte obligatoria une la 7.1 (red interna) y la 7.2
> (cortafuegos); la parte voluntaria (sin entrega) recoge la 7.3 (router/NAT).

#### Actividad 7.1 — Configuración de una red interna y del cortafuegos

- **Cambia el título:** «Creación de una red interna» → «Configuración de una red
  interna y del cortafuegos».
- **Tiempo:** 1 h + 1 h → **2 h** (suma de la 7.1 y la 7.2 de la agenda).
- **Parte obligatoria:** une la 7.1 y la 7.2:
  - Bridge `vmbr100` con `10.0.0.100/24`.
  - VM `router` con `vmbr0` y `vmbr100`, interfaz interna `10.0.0.1/24`.
  - CT `cliente` en `vmbr100` con `10.0.0.2/24`, gateway `10.0.0.1`.
  - `ping` desde el router al contenedor.
  - Servidor web en `router` y cortafuegos con regla TCP/80.
- **Recomendaciones de la 9:**
  - Debian 11 → **Debian 13**; el router se puede crear con un clon o plantilla.
  - Activar el cortafuegos en **VM → Firewall → Options → Enable** y marcar la
    casilla **Firewall** de la NIC conectada a `vmbr0` (no está en *Hardware*).
  - El cortafuegos del Datacenter puede seguir desactivado; el del nodo viene
    activado por defecto.
  - No hace falta activar el cortafuegos **nftables** en *technology preview*.
  - Si se hace con un usuario sin privilegios, hace falta `SDN.Use` sobre el
    bridge (ver módulo 8).
- **Pantallazos:** `ip a` en `router`, *Networks* de `cliente`, `ping` de `router`
  a `cliente`, reglas del cortafuegos con la regla TCP/80 y acceso al servidor web
  desde el navegador. Se sustituye el pantallazo de *Hardware* del router por el de
  `ip a`, que muestra las dos interfaces y sus IPs.
- **Parte voluntaria (No hay que entregar nada):** recoge la 7.3:
  - Activar forwarding (`net.ipv4.ip_forward=1`).
  - SNAT con `iptables` (o `nft`) para que `cliente` salga a Internet.
  - Comprobar con `ping 1.1.1.1` desde `cliente`.
  - Nota: en Debian 13 comprobar los nombres de interfaz; si se usa
    NetworkManager, la regla `post-up` de `/etc/network/interfaces` no se aplica.
  - Alternativa: usar el **SNAT** de una subred SDN.
- **Texto propuesto:**

  ```markdown
  # ACTIVIDAD Nº 1

  ## TÍTULO DE LA ACTIVIDAD: Configuración de una red interna y del cortafuegos

  ## TEXTO DE LA ACTIVIDAD

  En esta actividad vamos a crear una red interna, conectar una máquina virtual y
  un contenedor LXC a ella, y configurar el cortafuegos de la máquina virtual. Para
  ello:

  1. Crea un bridge llamado `vmbr100` y configúralo con la IP `10.0.0.100/24`.
  2. Crea una máquina virtual llamada `router`, con una interfaz conectada a
     `vmbr0` y otra a `vmbr100`. Puedes crearla a partir de un clon o de una
     plantilla de Debian 13.
  3. Configura la interfaz conectada a `vmbr100` de forma estática con la
     dirección `10.0.0.1/24`.
  4. Crea un contenedor LXC llamado `cliente`, conectado a `vmbr100`. Configura su
     interfaz de forma estática con la IP `10.0.0.2/24` y gateway `10.0.0.1`.
  5. Ejecuta un `ping` desde la máquina `router` al contenedor `cliente` para
     comprobar la conectividad.
  6. Instala un servidor web en la máquina `router`.
  7. Activa el cortafuegos de la máquina `router` y la casilla **Firewall** de la
     interfaz conectada a `vmbr0`.
  8. Comprueba que no tienes acceso al servidor web desde el exterior.
  9. Crea una regla de cortafuegos de entrada para permitir el puerto 80 del
     protocolo TCP.
  10. Comprueba que ya tienes acceso al servidor web desde el exterior.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  1. Un pantallazo de la salida del comando `ip a` en la máquina `router`, para
     comprobar las direcciones IP de las interfaces.
  2. Un pantallazo del apartado **Networks** del contenedor `cliente`.
  3. Un pantallazo de la salida del comando `ping` desde `router` a `cliente`.
  4. Un pantallazo de las reglas del cortafuegos de `router`, donde se vea la regla
     del puerto 80.
  5. Un pantallazo del acceso al servidor web desde un navegador web.

  ## Parte voluntaria (No hay que entregar nada)

  En esta parte vamos a configurar el router/NAT para que el contenedor `cliente`
  tenga acceso a Internet. Esta parte es voluntaria y no hay que entregar nada:

  1. En `router`, activa el forwarding: descomenta `net.ipv4.ip_forward=1` en
     `/etc/sysctl.conf` y ejecuta `sysctl -p`.
  2. Instala `iptables` y añade la regla de SNAT en `/etc/network/interfaces`:
     `post-up iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o ens18 -j MASQUERADE`
     (cambia `ens18` por el nombre de la interfaz conectada a `vmbr0`).
  3. Reinicia la interfaz y comprueba la regla con `iptables -L -n -t nat`.
  4. Desde `cliente`, comprueba el acceso a Internet con `ping 1.1.1.1`.

  ## RECURSOS

  * Conexión a Internet

  ## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

  Sí

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

  * Se entregan los documentos, contienen lo solicitado y los contenidos son
    originales.

  ## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

  No

  ## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

  2 horas
  ```

- **Ficheros:** `actividad1.md` queda con todo; se eliminan `actividad2.md` y
  `actividad3.md`.

### Módulo 8

#### Actividad 8.1 — Gestión de usuarios

- **Se mantiene obligatoria**, pero **2 h** (coincide con la agenda del
  `README.md`; el fichero dice 1 h).
- Mantener la posibilidad de elegir uno de los dos ejemplos.
- **Cambio imprescindible en el Ejemplo 2:** dar a `alumno1` y `alumno2` el rol
  **`PVESDNUser`** sobre `/sdn/zones/localnetwork` (o sobre el bridge concreto).
  Sin ese permiso, el asistente de creación de VM deja el campo **Bridge** vacío y
  no deja continuar.
- **Resto de permisos:** los roles de cada ejemplo (`Administrator`, `PVEAuditor`,
  `PVEDatastoreUser`, `PVEVMAdmin` y `PVEPoolUser`) y las rutas están explicados en
  `ejemplo1.md`, `ejemplo2.md`, `permisos.md` y `pools.md`. `PVESDNUser` es el
  permiso adicional para conectar las máquinas a la red.
- En el **Ejemplo 1**, los operadores ya necesitan `PVESDNUser` sobre
  `/sdn/zones` si van a crear máquinas; solo es necesario si la actividad prueba
  esa operación.
- Añadir un pantallazo del permiso de red en el Ejemplo 2:
  **localnetwork → Permissions → Add → User Permission**, con rol
  `PVESDNUser`.
- Recordar que los usuarios ven un menú *Datacenter* reducido (Search, Users,
  API Tokens, Two Factor); no es un error.
- Dependencias: ninguna, aunque conviene haber hecho el módulo 7 para entender
  `localnetwork`.
- **Texto propuesto:**

  ```markdown
  # ACTIVIDAD Nº 1

  ## TÍTULO DE LA ACTIVIDAD: Gestión de usuarios

  ## TEXTO DE LA ACTIVIDAD

  Elige uno de los dos ejemplos que se han presentado en los contenidos,
  configúralo en tu entorno de Proxmox y comprueba su funcionamiento.

  **Nota:** los usuarios que no son administradores ven un menú *Datacenter*
  reducido (Search, Users, API Tokens y Two Factor). Es normal.

  Para superar la actividad deberás entregar en un fichero comprimido los
  siguientes pantallazos:

  Si has elegido el **Ejemplo 1: Especificar tipos de usuarios**, entrega:

  1. Un pantallazo accediendo con el usuario `user1` y comprobando que puedes ver
     las estadísticas (opción **Summary**) del nodo del clúster.
  2. Un pantallazo accediendo con el usuario `user2` y comprobando que no es
     posible visualizar las estadísticas (opción **Summary**) del nodo del
     clúster.
  3. Un pantallazo accediendo con el usuario `user3` y comprobando que no puede
     crear máquinas virtuales.

  Si has elegido el **Ejemplo 2: Aislamiento de usuarios**, entrega:

  1. Un pantallazo de los permisos de red de `alumno1` (o `alumno2`) en
     `localnetwork`, donde se vea el rol **`PVESDNUser`**. Sin este permiso, el
     asistente de creación de la máquina deja el campo **Bridge** vacío y no deja
     continuar.
  2. Un pantallazo accediendo con el usuario `alumno1` y donde se vea que ha
     creado una máquina (no hace falta instalarla) en su pool de recursos.
  3. Un pantallazo accediendo con el usuario `alumno2` y donde se vea que ha
     creado una máquina (no hace falta instalarla) en su pool de recursos.
  4. Un pantallazo accediendo con el usuario `profesor1` y donde se vean los pools
     de recursos de los dos usuarios alumnos.

  ## RECURSOS

  * Conexión a Internet

  ## ¿ES OBLIGATORIO HACER ESTA ACTIVIDAD PARA SUPERAR EL CURSO? (S/N)

  Sí

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

  * Se entregan los documentos, contienen lo solicitado y los contenidos son
    originales.

  ## ¿ES NECESARIO TENER TERMINADA ALGUNA ACTIVIDAD O RECURSO ANTERIOR? Indique cuáles.

  No

  ## TIEMPO ESTIMADO PARA REALIZAR LA ACTIVIDAD

  2 horas
  ```

---

## Cambios en el `README.md` y en la agenda

Si se aprueba la propuesta:

1. **Módulo 3:** dejar una sola entrada de actividad en el índice:
   «Actividad 3.1: Creación de máquinas virtuales (OBLIGATORIA)». Eliminar las
   entradas 3.2, 3.3 y 3.4.
2. **Agenda del módulo 3:** eliminar la línea de la actividad 3.2 y actualizar el
   título y el tiempo de la 3.1 a 2 h. La 3.2 ya no es una actividad evaluable.
3. **Módulo 4:** dejar una sola entrada de actividad en el índice:
   «Actividad 4.1: Gestión del almacenamiento con Proxmox (OBLIGATORIA)».
   Eliminar las entradas 4.2 y 4.3. En la agenda, eliminar la línea de la 4.2 y
   actualizar el título y el tiempo de la 4.1 a 2 h.
4. **Módulo 5:** dejar una sola entrada de actividad en el índice:
   «Actividad 5.1: Clonación, plantillas, instantáneas y copias de seguridad
   (OBLIGATORIA)». Eliminar las entradas 5.2, 5.3 y 5.4. En la agenda, eliminar la
   línea de la 5.2 y actualizar el título y el tiempo de la 5.1 a 2 h.
5. **Módulo 6:** dejar una sola entrada de actividad en el índice:
   «Actividad 6.1: Creación y almacenamiento de un contenedor LXC
   (OBLIGATORIA)». Eliminar la entrada 6.2. En la agenda, eliminar la línea de la
   6.2 y actualizar el título y el tiempo de la 6.1 a 2 h.
6. **Módulo 7:** dejar una sola entrada de actividad en el índice:
   «Actividad 7.1: Configuración de una red interna y del cortafuegos
   (OBLIGATORIA)». Eliminar las entradas 7.2 y 7.3. En la agenda, eliminar la
   línea de la 7.2 y actualizar el título y el tiempo de la 7.1 a 2 h.
7. **Horas:**
   - 2.1: 1 h → 2 h en el fichero de la actividad.
   - 3.1: 1 h → 2 h en el fichero y en la agenda (decidido).
   - 4.1: 1 h → 2 h en el fichero y en la agenda.
   - 5.1: 1 h + 1 h → 2 h en el fichero y en la agenda.
   - 6.1: 1 h + 1 h → 2 h en el fichero y en la agenda.
   - 7.1: 1 h + 1 h → 2 h en el fichero y en la agenda.
   - 8.1: 1 h → 2 h en el fichero de la actividad.
8. **Títulos:** unificar el formato de los títulos de las actividades con el
   estado entre paréntesis (`(OBLIGATORIA)` / `(VOLUNTARIA)`), igual que el
   índice y la agenda.
9. **Texto:** sustituir «1Gb»/«2Gb» por «1 GiB»/«2 GiB» y «Debian 11» por
   «Debian 13».

## Decisiones que debe tomar el autor

1. **Parte optativa de Windows:** ¿se mantiene el texto completo de los pasos o se
   resume? La propuesta es mantener los pasos esenciales, sin entrega.
2. **SDN opcional:** ¿se incluye la alternativa SNAT del SDN en la parte voluntaria
   del módulo 7? La propuesta es mencionarla como alternativa, sin cambiar la vía
   obligatoria (Linux Bridge).
3. **Módulo 5:** ¿la parte voluntaria va sin entrega, como la del módulo 4, o
   mantiene los pantallazos de las 5.3 y 5.4? La propuesta es sin entrega.
4. **Títulos y dependencias:** ¿se unifican los títulos con el estado y se
   corrigen las dependencias? La propuesta es sí.

## Checklist para aplicar la propuesta (cuando se apruebe)

- [ ] Actualizar `modulo1/actividad1.md` (sin cambios de contenido).
- [ ] Actualizar `modulo2/actividad1.md`: tiempo a 2 h y nuevo paso 2 con las dos alternativas.
- [ ] Actualizar `modulo3/actividad1.md`: nuevo título, tiempo de 2 h, integrar
      la 3.3 y añadir la «Parte optativa (No hay que entregar nada)» con Windows 11.
- [ ] Eliminar `modulo3/actividad2.md`, `modulo3/actividad3.md` y
      `modulo3/actividad4.md` (contenido fusionado o eliminado).
- [ ] Actualizar `modulo4/actividad1.md` a «Gestión del almacenamiento con
      Proxmox» (fusionar 4.1 + 4.2, 2 h, y añadir la parte voluntaria: gestión
      del disco de la parte obligatoria + VM nueva con disco en el pool, sin
      entrega) y eliminar `actividad2.md` y `actividad3.md`.
- [ ] Actualizar `modulo5/actividad1.md` a «Clonación, plantillas, instantáneas y
      copias de seguridad» (fusionar 5.1 + 5.2 en la parte obligatoria y 5.3 + 5.4
      en la voluntaria sin entrega, 2 h) y eliminar `actividad2.md`,
      `actividad3.md` y `actividad4.md`.
- [ ] Actualizar `modulo6/actividad1.md` a «Creación y almacenamiento de un
      contenedor LXC» (fusionar 6.1 + 6.2, 2 h) y eliminar `actividad2.md`.
- [ ] Actualizar `modulo7/actividad1.md` a «Configuración de una red interna y del
      cortafuegos» (fusionar 7.1 + 7.2 en la parte obligatoria y 7.3 en la
      voluntaria sin entrega, 2 h) y eliminar `actividad2.md` y `actividad3.md`.
- [ ] Actualizar `modulo8/actividad1.md` (`PVESDNUser` y tiempo).
- [ ] Actualizar el índice y la agenda del `README.md`.
- [ ] Revisar que las actividades no se contradicen con el contenido de los
      módulos actualizados.
- [ ] No tocar los `.elp` (las actividades no están incluidos en ellos).

## Notas prácticas de laboratorio

- Con 100 GB de disco, Windows 11 (64 GiB) + Debian 13 (32 GiB) + ISOs + copias de
  seguridad puede quedarse corto. Para las actividades 5.x es mejor usar la VM
  Debian y no la de Windows.
- No mantener encendidas a la vez la VM Windows y varias VM Linux; con 8 GB de RAM
  el sistema se ralentiza mucho.
- Antes de clonar en `local-lvm`, apagar la VM: en caliente, el clon puede copiar
  los 32 GiB completos y llenar el thin pool.
- Las copias de seguridad y los clones antiguos se pueden borrar entre módulos
  para recuperar espacio.
