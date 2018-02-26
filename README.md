SDR_Dongle
==============

- 	[Introducción](#introducción)

-	[Precauciones](#precauciones)

-	[Sigfox Network Emulator-Windows](#sigfox-network-emulator-windows)

	-	[Requerimientos Windows](#requerimientos-windows)

	-	[Instalación](#instalación)

	-	[SNE](#sne)

-	[Radio Signal Analizer](#radio-signal-analizer)

	- 	[Requerimientos RSA](#requerimientos-rsa)

	-	[Booteable](#booteable)

-	[Procedimiento macOS](#procedimiento-macos)

	-	[Requerimientos macOS](#requerimientos-macos)

	-	[Memoria booteable](#memoria-booteable)

	-	[Inicializando Ubuntu](#inicializando-ubuntu)

	-	[Instalación SNE](#instalación-sne)



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

Sigfox Network Emulator-Windows
-------------------------------

Esta herramienta permite probar dispositivos de otras zonas diferentes a la zona en la que nos encontremos, por lo que si nuestro dispositivo bajo prueba no tiene conector SMA o UFL, podemos ponerle una antena a nuestro SDR Dongle para que pueda recibir los mensajes enviados por el dispositivo, asegurándonos que la distancia entre los 2 sea mayor a 50 cm para evitar saturación.

### Requerimientos Windows

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

Radio Signal Analyzer
---------------------

Esta herramienta nos permite analizar en tiempo real las señales de dispositivos Sigfox. Puede decodificar los mensajes y analizar la señal RF del dispositivo (Modulación, demodulacion, precisión de la velocidad de datos, precisión de fase, etc.) El software compara los resultados con los requerimientos de Sigfox y permite hacer una pre certificación del dispositivo. Esto no remplaza ninguna certificación realizada en un laboratorio certificado y aprobado por Sigfox.

### Requerimientos RSA

-	1 cable SMA/SMA o 1 cable SMA/UFL

-	1 atenuador (40 dB)

-	1 memoria USB con mínimo 2 GB disponibles

-	2 GB de memoria RAM mínimo

-	Computadora con procesador de 64 bits

-	Archivo .iso ([LINK](https://support.sigfox.com/downloads/sigfoxradiosignalanalyzer.iso))

-	Software para crear la memoria booteable [UNetBootin](https://unetbootin.github.io/)

### Booteable

Una vez descargado el archivo .iso y UNetBootin de acuerdo a nuestro sistema operativo, ejecutamos UNetBootin el cual no requiere de instalación. Enseguida nos aparecerá un recuadro donde seleccionaremos el archivo .iso y nuestra memoria USB. Igualmente configuramos cuanta memoria asignaremos a Ubuntu. 

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/boot1.png)

Click en OK y esperamos a que termine el proceso de instalación.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/boot2.png)

Una vez completado, apagamos nuestra computadora. 

Para los siguientes pasos, antes de que arranque el sistema operativo, debemos modificar el lugar desde donde arrancará, por lo que necesitamos entrar al BIOS y modificar las opciones de arranque.

Para este ejemplo se utilizará una laptop VAIO, por lo que para entrar al BIOS, dejamos presionado F2 al momento de encender la maquina (Dependiendo de la marca, varia la tecla que debemos presionar)

Una vez dentro, configuramos para que la primera opción de arranque sea la memoria USB ya booteada. Nos vamos a la pestaña “Boot” y habilitamos la opción para el arranque a partir de dispositivos externos y le damos la prioridad mas alta a “dispositivos externos”. Guardamos y salimos.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/init1.png)

Enseguida, nos aparecerá un menú, donde seleccionaremos “Try Ubuntu MATE without installing”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/init2.png)

e inmediatamente después, empezará a cargar Ubuntu

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/init3.png)

Una vez inicializado, veremos el escritorio donde visualizaremos el programa para el “Radio Signal Analyzer”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/ubuntu1.png)

Ejecutamos el programa y aceptamos el acuerdo de la licencia

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/ubuntu2.png)

Ahora ya podemos realizar pruebas de medición de la señal RF de un dispositivo.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/ubuntu3.png)

para mas información sobre los diferentes test revisar la siguiente documentación:

-	[Radio Signal Analizer-User guide](https://storage.sbg1.cloud.ovh.net/v1/AUTH_669d7dfced0b44518cb186841d7cbd75/staging_docs/att14428358-Radio%20Signal%20Analyser_user%20guide.pdf)

Procedimiento macOS
-------------------

A continuación se muestra el procedimiento para macOS, desde crear la memoria booteable con Ubuntu Mate hasta instalar el programa para el SNEK. 

### Requerimientos macOS

-	1 memoria USB con mínimo 2 GB disponibles

-	Computadora con procesador de 64 bits

-	2 GB de memoria RAM mínimo 

-	Archivo .iso ([LINK](https://support.sigfox.com/downloads/sigfoxradiosignalanalyzer.iso))

-	Software para crear la memoria booteable [UNetBootin](https://unetbootin.github.io/) para macOS

-	Memoria extra con el ejecutable del SNEK para Ubuntu ([Link](https://support.sigfox.com/downloads/snek.deb))

### Memoria booteable

Una vez descargados los dos archivos (.iso y UNetBootin), damos doble click en el archivo de UNetBootin

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot1.png)

nos aparecerá una ventana con dos iconos. Damos doble click en el icono de “unetbootin”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot2.png)

enseguida, se mostrará un cuadro de dialogo diciéndonos que no se puede abrir porque proviene de un “desarrollador no identificado”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot3.png)

hacemos click en “OK”. Abrimos  Preferencias del Sistema -> Seguridad y Privacidad 

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot4.png)

damos click en “Abrir de todos modos”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot5.png)

enseguida aparecerá un cuadro de dialogo. Click en “Abrir”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot6.png)

ingresamos nuestra contraseña para realizar los cambios

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot7.png)

a continuación intentamos volver a abrir “unetbootin”, en dado caso que no se abra automáticamente. Seleccionamos el archivo .iso descargado, asignamos cierta cantidad de MB para el sistema operativo (se usaron 200 MB para este ejemplo) y seleccionamos la memoria donde montaremos la imagen ISO. Click en “OK”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot8.png)

Enseguida empezará a extraer y copiar los archivos a nuestra memoria. Después de unos minutos, terminará de preparar la memoria booteable. Damos click en “Exit”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macboot9.png)

Con eso ya tenemos nuestra memoria lista para arrancar el sistema operativo Ubuntu con la aplicación del RSA.

### Inicializando Ubuntu

Para arrancar el sistema operativo desde nuestra memoria, es necesario cambiar el origen. Procedemos a apagar nuestra maquina. Una vez apagada, conectamos la memoria booteable y presionamos la tecla “alt”. 


Sin dejar de presionar encendemos nuestra computadora. Nos aparecerá un menú donde seleccionaremos el origen del sistema operativo que deseamos cargar. 

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/boot22.jpeg)


Seleccionamos la memoria booteable y después seleccionamos “Try Ubuntu MATE without installing”. 

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/boot23.jpeg)

después de unos minutos, empezará a cargar el sistema operativo desde la memoria

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/ubuntu1.png)

### Instalación SNE

Para instalar el programa para el SNE, conectamos nuestra otra memoria con el ejecutable del SNEK.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macsne1.png)

ejecutamos el programa dando doble click y nos aparecerá una ventana. Hacemos click en “Install Package”

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macsne2.png)

introducimos la contraseña, la cual es “rsa”. Aceptamos los términos de la licencia y damos click en Forward 

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macsne3.png)

después de unos minutos, terminará la instalación. Click en close, y cerramos las demás ventanas.

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macsne4.png)

Conectamos nuestro SDR Dongle y nos vamos a Applications -> Internet -> Sigfox Network Emulator. Lo ejecutamos y se abrirá en algún navegador

![down3](https://github.com/Iotnet/SDR_Dongle/blob/master/imagenes/macsne5.png)








