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

Hemos visto como se realiza las operaciones con las entradas o salidas digitales. Las cuales solo pueden tener 2 valores o 0 o 1. Sin embargo, normalmente se tienen valores distintos de este 0 o 1. Por lo que se utilizan las entradas o salidas analógicas.

Estas entradas permiten leer o escribir valores distintos de 0 o 1. En micropython se pueden utilizar estas entradas o salidas anlógicas.

Es importante conocer como funciona la lectura analógica; ya que el microcontrolador como puede ser el ESP32, utiliza lógica binaria; por lo que es necesario algún mecanismo para poder trabajar con la lógica analógica. Es por esto que el microcontrolador tiene un dispositivo llamado ADC(Analog digital Converter) el cual permite transformar de un valor analógico a un valor digital. Esto se realiza realizando una división en niveles de distintos voltajes entre el 0 y el 1. (entre 0 y 3.3V).

En la placa NodeMCU podemos ver que para el modelo con la ESP32, tiene varias entradas analógicas; esto lo podemos ver en su pinout; que puede encontrarse al final de este libro.

En micropython, para usar la lectura analógica, usaremos la clase ```ADC``` del modulo ```machine```. Esta clase nos permitirá leer un valor de entre 0 y 1023; ya que la precisión del conversor ADC de la placa es de 10 bits.

```python
from machine import ADC
ADC adc = ADC(0)
```
Donde el número 0 indica el número de entrada analógica. Para saber cual usar, consultaremos de nuevo el pinoput.

Para leer un valor, usaremos la función ```read()```. El cual nos devuelve un valor entre 0 y 1023.

```python
from machine import ADC
ADC adc = ADC(0)
adc.read()
```

Una vez visto como leer un valor analógico, vamos a pasar a escribir un valor analógico. Esto se realiza gracias al PWM(Pulse With Modulation); se trata de una técnica que nos permite a partir de una serie de valores de alto y bajo (0 o 1)en el tiempo poder calcular un valor analógico. Con el PWM se permite calcular un valor de entre 0 y 1023; ya que también se tiene una precisión de 10 bits.

Para usar el PWM en micropython, se utilizará la clase ```PWM``` del módulo ```machine```.  En esta clase podemos cambiar el ciclo por segundo (muestras por segundo) y el valor que mostrará por el PWM.

```python
from machine import PWM, Pin

PWM pwm = PWM(Pin(5))
pwm.freq(60)
pwm.duty(512)
```

Como vemos en el código anterior, necesitamos crear un objeto de tipo ```Pin```; es importante saber que se puede utilizar cualquier Pin digital, excepto el Pin 16(D0) ya que este es necesario para una interrupción del sistema.

Una vez ya hemos visto como se utiliza el PWM, ya podemos pasar a conectar distintos periféricos por distintos protocolos.

## Periféricos

## Conectividad

## Ahorro de energia

## Concurrencia

## módulos micropython

## módulos especificos

