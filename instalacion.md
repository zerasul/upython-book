# Apéndice A: Instalación y configuración de MicroPython en la ESP32

Para poder instalar MicroPython, necesitaremos tener instalado Python 3.4 o superior. Cualquier instalación de Python sera suficiente. En nuestro caso recomendamos utilizar [Anaconda](https://anaconda.org); el cual es una herramienta que instala python y las librerías ms comunes; demas de tener una serie de herramientas para poder gestionar los entornos de desarrollo.

Para poder instalar anaconda, lo descargaremos de la página oficial https://www.anaconda.com/download/ y lo instalaremos. Una vez instalado, vamos a abrir una terminal para poder utilizar nuestro entorno python. Por ello utilizaremos la herramienta de _Anaconda Navigator_.

![anaconda-navigator](anaconda.png)

Una vez en la aplicación vamos a la pantalla de _Enviorements_; de manera que podemos crear un entorno de desarrollo, o usar el que viene por defecto. Una vez creado, pulsaremos en el botón de "play" y pulsaremos la opción _open Terminal_.

Antes de continuar, necesitaremos instalar la herramienta _esptool_ la cual nos permitirá flashear la placa de Desarrollo ESP32. Por lo que utilizaremos Pip para instalarla.

```bash
$ pip install esptool
```

## Flashear la placa de desarrollo

Una vez tenemos todo instalado ya podemos pasar a flashear la memoria de la ESP32; por lo que en primer lugar descargaremos la imagen correspondiente a nuestra placa ESP32 que puede descargarse de [http://micropython.org/download#esp32](http://micropython.org/download#esp32). Es importante descargar la imagen correspondiente a nuestro chip o placa. Por lo que descargaremos la correspondiente a la ESP32(Si tuvieramos que instalar la correspondiente a la ESP8266 se descargará la imagen de dicho chip).

### Linux

Para los Sistemas Linux no es necesario instalar un driver ya que viene por defecto.

### MacOs

Para los sistemas MacoS necesitaremos descargar el driver que puedes descargar de [http://www.mblock.cc/docs/run-makeblock-ch340-ch341-on-mac-os-sierra/](http://www.mblock.cc/docs/run-makeblock-ch340-ch341-on-mac-os-sierra/).

### Windows

Para los sistemas Windows tambien es necesario descargar el driver de la dirección [http://www.wch.cn/download/CH341SER_EXE.html](http://www.wch.cn/download/CH341SER_EXE.html).

Una vez descargada la imagen e instalado el driver, pasaremos a borrar la memoria del chip con la herramienta _esptool_. Sin embargo, en función del sistema operativo que tengamos, necesitaremos instalar los drivers para que nuestro sistema detecte la placa como un puerto serie.


```bash
$ esptool.py /dev/ttyUSB1 erase_flash
```
En el comando anterior, tenemos que saber que puerto utilizar en el caso de Linux y MacoS; pero para sistemas Windows, tenemos que utilizar el puerto COM correspondiente; el cual podemos ver en el administrador de dispositivos.

Una vez borrada la memoria del chip ya podemos flashear la imagen que hemos descargado anteriormente.

```bash
esptool.py --chip esp32 --port /dev/ttyUSB1 write_flash -z 0x1000 firmware-ESP32.bin
```

El comando anterior, flashea la imagen correspondiente a la placa con el ESP32 el cual necesita la imagen descargada y se indica que debe empezar por la dirección 0x1000 y el chip corresponde al esp32.

Si por un casual requiere el uso de la ESP8266, se usará el siguiente comando.

```bash
$ esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 esp8266-20170108-v1.9.2.bin
```
El comando anterior puede dar un error de timeout; por lo que recomendamos en dicho caso usar una velocidad de 115200 baudios.

