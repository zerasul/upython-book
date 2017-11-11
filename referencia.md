# Apéndice B: Referencia MicroPython para la ESP32.

Este este apéndice se mostrará información sobre el uso de las funciones más comunes a la hora de aplicarla tanto a la electrónica básica,
como al uso en proyectos de Internet de las Cosas. Todo ello dentro del ámbito del chip de la ESP32.

Toda la referencia la veremos con respecto a su uso dentro de la electrónica básica y como utilizarlo en cada caso. Comenzando por las
entradas/salidas digitales y también veremos como poder comunicarnos con periféricos y por supuesto como utilizar la conectividad tanto de red,
como de Bluetooth ya que la ESP32 trae soporte para los dos.

## Entrada/Salida Digital

El primer paso a la hora de trabajar con electrónica es el uso de entradas y salidas digitales. En el caso de los microcontroladores se pueden usar estas entradas o salidas para poder mandar señales o recibir señales del exterior. 

A la hora de trabajar con el microcontrolador ESP32, podemos usar varias entradas o salidas como digitales. Por ello tenemos que conocer la placa que vamos a utilizar ya que puede cambiar en función de la placa donde se encuentre.

Para este libro tomamos como referencia la placa NodeMCU con su versión con el microcontrolador ESP32.

Una vez sabemos la placa que usaremos en este libro, podemos ver los pines y como se compone esta placa.

Puede ver una imagen del Pinout al final de este [libro](pinout.md).

Para poder usar con micropython las entradas o salidas digitales, pueden usar la clase ```Pin``` dentro del modulo ```machine```. Esta clase permite actuar con un pin a partir del número del GPIO que puede verse en el Pinout.

```python
import machine

pin0 = machine.Pin(4, machine.Pin.OUT)
```

En el código anterior, usamos el pin 4 como salida de forma que podriamos mandar una señal desde el controlador.

```python
pin0.on()
```

De forma que para el caso anterior, mandamos una señal desde el pin0, usando la función ```on()```.

Para apagarlo usaremos la función ```off()```. Con esto ya podemos usar una salida del microcontrolador de forma analógica.

En el caso de querer usar una entrada, podemos activar una resistencia de _PULL_UP_ para que en algunos casos evitar falsos positivos o proteger el microcontrolador.

```python
from machine import Pin
boton = Pin(23, Pin.IN, Pin.PULL_UP)
```

En el caso anterior, vemos que usaremos el GPIO23, de manera que es una entrada y activamos la resistencia de Pull up. de forma que podemos detectar cuando esta entrada recibe un 1 o un 0. Para ello se utiliza la función ```value()``` de forma que podemos leer el valor que tiene dicha entrada.

```python
boton.value()
```

La función ```value()``` también podemos usarla para establecer el valor de un pin de salida.

```python
from machine import Pin

led = Pin(16, Pin.OUT)

led.value(1)
```

Una vez visto como se puede utilizar la entrada/ salida digital, pasaremos a utilizar entradas o salidas analógicas.

## Entrada/Salida Analógica

## Periféricos

## Conectividad

## Ahorro de energia

## Concurrencia

## módulos micropython

## módulos especificos

