SDR_Dongle
==============

- 	[Introducción](#introducción)

-	[Precauciones](#precauciones)

-	[Sigfox Network Emulator](#sigfox-network-emulator)

	-	[Requerimientos](#requerimientos)

	-	[Instalación](#instalación)

	-	[SNE](#sne)

Introducción
------------

El SDR Dongle de Sigfox es una herramienta que permite emular el Backend sin necesidad de una cuenta ni de registrar los dispositivos. Esto permite probar y desarrollar dispositivos de otras zonas. Además, tambien permite analizar el patrón de radiación de nuestros dispositivos de manera que podamos prepararlo para los test de certificación.

La caja del SDR Dongle contiene:

-	1 SDR Dongle de Sigfox con conector SMA.

-	1 cable SMA/SMA.

- 	1 cable SMA/UFL.

- 	1 atenuador de 40 dB.

![sdr1](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sdr1.png)

Precauciones
------------

ADVERTENCIA: Para realizar las pruebas con el RSA (Radio Signal Analyzer) o con el SNE (Sigfox Network Emulator) conectando nuestro dispositivo por medio de un cable, es necesario siempre conectar el atenuador de 40 dB como se muestra en la imagen de  abajo para evitar daños en el SDR Dongle.

![sdr2](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sdr2.png)

Sigfox Network Emulator
-----------------------

Esta herramienta permite probar dispositivos de otras zonas diferentes a la zona en la que nos encontremos, por lo que si nuestro dispositivo bajo prueba no tiene conector SMA o UFL, podemos ponerle una antena a nuestro SDR Dongle para que pueda recibir los mensajes enviados por el dispositivo, asegurándonos que la distancia entre los 2 sea mayor a 50 cm para evitar saturación.

### Requerimientos

-	Software emulador, el cual está disponible para Windows 7 y 10 ([Link](https://support.sigfox.com/downloads/snek.exe)) y para Ubuntu 16.04 ([Link](https://support.sigfox.com/downloads/snek.deb))

NOTA 1: Para usuarios de Linux, asegurarse de estar en el grupo ”plugdev”.

NOTA 2: Los navegadores soportados son Google Chrome y Mozilla Firefox.

### Instalación

Una vez descargada la versión para nuestro sistema operativo, lo ejecutamos como administrador. En este caso se hará para Windows 7.

![inst1](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst1.png)

enseguida aparecerá una ventana para iniciar con el proceso de instalación. Click en “Next”

![inst2](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst2.png)

aceptamos el acuerdo de la licencia y damos click en “Next”

![inst3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst3.png)

seleccionamos la ruta donde se va instalar. Por defecto lo hace en “Archivos de Programa”. Click en “Next”

![inst4](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst4.png)

después de unos minutos, la instalación finalizará. Click en “Finish”

![inst5](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst5.png)

Ahora que ya tenemos instalado el software, conectamos el SDR Dongle a nuestra computadora. Abrimos el menú de inicio Inicio, y buscamos el programa “Sigfox Network Emulator”.

![inst6](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/inst6.png)

Al ejecutar el programa, se abrirá en nuestro navegador. (Recargar la página en dado caso que no se abra de forma correcta).

### SNE

Ahora, lo primero es configurar la region. Para este ejemplo se utilizará un dispositivo el cual es Zona 1 (868 MHz), pero se puede utilizar cualquier otro dispositivo de otra región (RC2, RC3 o RC4). 

Seleccionamos la region de nuestro dispositivo, para este caso RC1 en “Radio Configuration” y automáticamente configurará los otros parametros. Damos click en “Save”

![sne1](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sne1.png)

Ahora seleccionamos la pestaña de “Devices” y escribimos el ID de nuestro dispositivo junto con un nombre. Podemos registrar hasta 5 dispositivos los cuales se pueden modificar en cualquier momento. Click en “Save”

![sne2](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sne2.png)

Una vez guardada la configuración, nos vamos a la pestaña de “Messages” y deshabilitamos la opción de autenticación.

![sne3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sne3.png)

Una vez que nuestro dispositivo mande un mensaje, este se verá reflejado en los mensajes

![sne4](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/sne4.png)

### Downlinks

Para realizar downlinks, es necesario cambiar el dispositivo de “Private Key” a “Public Key” o conocer la clave de autenticación del dispositivo. 

Seleccionamos la pestaña de “Callbacks” lo configuramos. Para este caso, se utilizará la configuración por default. 

![down0](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/down0.png)

Configuramos la zona de nuestro dispositivo y damos click en “Save”

![down1](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/down1.png)

Agregamos nuestro dispositivo

![down2](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/down2.png)

Realizamos una petición de downlink desde nuestro dispositivo y esperamos a que se realice de forma exitosa.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/down3.png)

Finalmente, para cerrarlo, damos click en el icono de “Apagar” en la esquina superior derecha y cerramos la pestaña del navegador.

Radio Signal Analyser
---------------------

Esta herramienta nos permite analizar en tiempo real las señales de dispositivos Sigfox. Puede decodificar los mensajes analizar la señal RF del dispositivo (Modulación, demodulacion, precisión de la velocidad de datos, precisión de fase, etc.) El software compara los resultados con los requerimientos de Sigfox y permite hacer una pre certificación del dispositivo. Esto no remplaza ninguna certificación realizada en un laboratorio certificado y aprobado por Sigfox.

### Requerimientos

-	1 cable SMA/SMA o 1 cable SMA/UFL

-	1 atenuador (40 dB)

-	1 memoria USB con mínimo 2 GB disponibles

-	2 GB de memoria RAM mínimo

-	Computadora con procesador de 64 bits

-	Archivo .iso ([LINK](https://support.sigfox.com/downloads/sigfoxradiosignalanalyzer.iso))

-	Software para crear la memoria booteable [UNetBootin] (https://unetbootin.github.io/)



