# Introducción

En este libro podrá encontrar información para realizar una serie de proyectos del denominado Internet de las Cosas de forma que podrá conectar distintos dispositivos y poder controlarlo a distancia a través de Internet, o poder mandar información de este a Internet.

## Objetivos

Los Objetivos de este libro son:

* Aprender a crear proyectos de electrónica básica utilizando Hardware libre y componentes básicos de electrónica.
* Utilizar Python para poder crear proyectos de electrónica usando la implementación para microcontroladores MicroPython.
* Aprender a utilizar la placa de desarrollo ESP32 para poder crear proyectos de electrónica y de Internet de las cosas (IoT).

## Hardware Libre

El _Hardware Libre_ o Hardware de Código abierto se refiere a los dispositivos cuyo diseño, especificaciones y diagramas esquemáticos son de dominio público o con una condiciones. Junto al _Software Libre_ forma parte de la cultura libre de forma que cualquier especificación de Hardware libre soporta la filosofía del software; excepto que el uso de Hardware conlleva algún tipo de gasto de fabricación o diseño. Adems de traer herramientas para compilación y ejecución proporcionándonos un entorno interactivo.

En este libro se utilizan componentes de Software y Hardware libre como puede ser el uso del chip ESP32 o sus variantes ESP8266. Todos los diseños que mostraremos en este libro son libres y pueden ser utilizados con respecto a la licencia de uso además de que pueden ser mejorados y compartidos siguiendo la filosofía de la cultura libre.

## MicroPython

MicroPython es una implementación ligera de lenguaje de programación Python en su versión 3.4 o superior. Esta implementación permite poder programar diferentes tipos de microcontrolador. MicroPython está pensado para entornos con muy pocos recursos como pueden ser los micrcontroladores de forma que se puede ejecutar en entornos con 256KB de memoria (aunque se recomienda 1MB) y 1KB de memoria RAM.

Existen implementaciones para distintas placas como puede ser la _pyboard_, _wipy_ y placas con el chip _ESPX_; como pueden ser la ESP8266 y la ESP32. Este libro se centra en la utilización de placas con el chip ESP32.

Aunque tienen muchas similitudes entre la ESP32 y la ESP8266, la ESP32 esta aún en desarrollo y no tiene todas las funcionalidades que tiene la ESP8266; como por ejemplo la conexión por WEBREPL.

Sin embargo, la ESP32 al tener un doble núcleo posee soporte para multiThreading; de forma que podemos crear hilos y hacer operaciones concurrentes. Esto se podrá ver en este libro.

Además, para ayudar al lector si no se tiene una ESP32, en muchos casos mostramos sentencias equivalentes para los chips ESP8266 de forma que sea totalmente compatible.

## ESP32

El ESP32 es un chip Soc(_System on a Chip_) de bajo coste y bajo consumo que tiene un procesador de doble núcleo con conectividad wifi y Bluetooth. Este chip permite con bajo coste crear proyectos del denominado Internet de las cosas ya que contiene una serie de funcionalidades como la conectividad Wifi, encriptación y comunicación con periféricos todos a nivel de Hardware.

Con su bajo coste ya que no suele costar más de 20 euros y que contiene una memoria de hasta 4MB nos permitirá utilizarlos en los proyectos con Micropython.

Hay que tener en cuenta la placa que usaremos como referencia para este libro en la cual tiene instalado el microcontrolador ESP32. En este libro vamos a utilizar como referencia la placa NodeMcu.

Seguidamente mostramos el diagrama de funcionalidades del chip ESP32.


![ESP32functionalDiagram](http://esp32.net/images/_resources/ESP32_Function_Block_Diagram.svg)
