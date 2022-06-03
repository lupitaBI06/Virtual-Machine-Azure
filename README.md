# Como crear Máquinas Virtuales (VM) en Azure 

Una máquina virtual es una emulación de software de equipos físicos (procesador virtual, memoria, alamecenamiento y recursos de red). Proporciona una infraestructura como servicio (IaaS) y son idóneas cuando se necesita un control total sobre el entorno y sistema operativo.

![logo de Máquina Virtual en Azure](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/virtual_machine_logo.png)

**¿Cuándo usar VM?**

- Durante las pruebas y el desarrollo.
- Al ejecutar aplicaciones en la nube.
- A la hora de extender el centro de recursos a la nube.
- Durante la recuperación ante desastres.
- Traslado a la nube.

----------------------------------------------------------------------------------------

#### Pasos para crear una máquina virtual en Azure

- El primer paso es entrar al [portal de Azure](www.portal.azure.com) 
- Una ves dentro del portal de Azure se elige crear recurso.

![crear recurso](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/crear_recurso.PNG)

- Se busca Máquinas Virtuales y se selecciona. 

![crear vm](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/vm.PNG)

- Una ves dentro deben completarse los 4 campos que son requeridos para crear cualquier recurso: Una suscripción, un grupo de recursos (crear uno si no se tiene), un nombre para el recurso y seleccionar una región. 

![requerimientos mínimos](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/requerimientos_minimos.PNG)

- Una ves llenados estos hay que terminar de llenar y seleccionar los demás requerimientos de datos generales.

![requerimientos generales](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/mas_requerimientos.PNG)
![requerimientos generales](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/mas_requerimientos2.PNG)

- En redes se deja todo como default (Debe estar seleccionado el grupo de seguridad de red si no la máquina no se puede abrir.)

![requerimientos redes](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/requerimientos_redes.PNG)

- Al finalizar de configurar la máquina virtual se da clic en el botón revisar y crear.

![revisar y crear](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/revisar_y_crear.PNG)

- Al terminar de revisar los campos requeridos, Azure despliega la información sobre la máuina virtual que se quiere crear, lo más importante es el costo que tiene la máquina solicitada. (Las máquinas virtuales cobran por hora).

![validación](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/validada.PNG)

- Una ves que se crea el recurso se muestra un mensaje como el siguiente, en el que se indica que todo se creó con éxito. 

![requerimientos generales](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/recurso_creado.PNG)

- Si nos vamos al grupo de recursos creado se pueden observar los componentes creados de la máquina virtual, la analogía con una PC física es la siguiente:
    - Red virtual y la IP pública -> Modem 
    - Máquina Virtual -> PC
    - Interfaz de red normal -> Wifi o Ethernet
    - Disco -> Disco de memoria 

![requerimientos generales](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/máquina_virtual_componentes.PNG)

Una ves la máquina virtual creada, se debe iniciar la conexión. Para esto se debe entrar al recurso VirtualMachine1 (nombre de la máquina virtual que se creo) y oprimir el conectar, se selecciona SDR.

![conectar vm](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/conectar.PNG)

Se debe descargar el archivo RDP.

![descargar archivo RDP](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/descargararchivo.PNG)

Una ves descargado hay dos formas de abrir la máquina virtual, la primera es descargando el escritorio remoto de Microsoft, este debe descargarse en la AppStore de Microsoft. La otra forma es abrirlos con Conexión a escritorio remoto ya instalado en Windows. 

El archivo descargado se abre con alguno de los programas anteriores, se le dan los permisos necesarios y si todo va bien pedirá el usuario y contraseña que se definieron en la creación de la máquina virtual. 

![abrir con escritorio remoto](imagenes\conexion escritorio remoto.PNG)

![usuario](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/usuario.PNG)

Si todo esta correcto, se empieza a abrir nuestra máquina virtual.

![vm](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/virtual_machine_funcionando.PNG)

Una práctica interesante es medir la velocidad del internet dentro de la máquina virtual. Esto se puede hacer mendiante el siguiente enlace [https://fast.com/es/](https://fast.com/es/). La máquina virtual creada cuenta con una velocidad de internet de 550 Mbps.

![internet](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/internetvm1.PNG)

#### Cómo conectar dos máquinas virtuales

Para conectar dos máquinas virtuales hay dos cosas importantes a considerar: las dos máquinas pueden estar en diferentes grupos de recursos y en regiones diferentes pero esto no se recomienda por que puede haber problemas de conexión. Para que se puedan conectar ambas deben estar en la misma red virtual. 

Si queremos conectar una máquina virtual a la máquina recien creada hay que verificar en la sección de red, que esté conectada a la misma red virtual.

![internet](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/VM2redes.PNG)

El resto del procedimeito para su creación es el mismo que se siguió en el apartado anterior.

Para comprobar la conexión de ambas máquinas virtuales se abre el cmd como administrador (dentro de la máquina virtual). Con la siguiente línea de comando se manda un ping que es el que ayuda a mandar unos paquetes a otra máquina conectada.

ping 10.0.0.5 (IP privada de la máquina virtual que recibe el paquete).

Si esto marca succes entonces indica que las conecciones estan bien.

Otra forma de verificar es mediante Power Shell, debe abrirse como adminisrador y se escriben las siguientes lineas para ejecutar el protocolo ICMPv4, este protocolo se usa para que se puedan conectar las máquinas virtuales.

![protocolo ICMPv4](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/ICMPv4.PNG)

Para abrir una máquina virtual dentro de otra máquina virtual se puede hacer con la siguiente linea en Power Shell (ejecutado como administrador).

![mstsc](https://github.com/lupitaBI06/Virtual-Machine-Azure/blob/main/imagenes/abrir_vm2_en_vm1.PNG)

Se muestran las dos máquinas virtuales una dentro de la otra.

![internet](imagenes\dos_máquinas_virtuales.PNG)
