# PROYECTO SISTEMA DE RIEGO

INTEGRANTES:

DIEGO ANDRES MIRANDA FERNANDEZ, ALVARO JOSE HERNANDEZ MARMOL, BRUSS ANDRES CORREA ROQUEME, JOSETH RODRIGUEZ CARDALES

FUNDAMENTOS DE PROGRAMACION

INGENIERIA ELECTRONICA

UNIVERSIDAD PONTIFICIA BOLIVARIANA

MONTERIA

2024


SISTESIS

Hoy en día, a muchas personas se les hace difícil estar pendientes de las plantas que tienen en su hogar debido a sus ocupaciones diarias. Como resultado, no siempre pueden regarlas a diario, y si las plantas no reciben agua regularmente, pueden morir. ¿Qué podemos hacer al respecto? Un sistema de riego automático que monitorea la humedad del suelo. Este sistema consta de una placa programable y varios sensores que permiten monitorear la humedad de la tierra. A través de operaciones automáticas, el sistema mantiene la planta bien regada, evitando que muera por falta de agua.

ANALISIS

PROBLEMA: Desarrollar un Sistema de riego Automatico que riegue una planta cuando la humedad de tierra sea baja y monitorear la cantidad de agua que hay en un dicho tanque y alertar al usuario cuando este en condicones criticas.

DETALLES: El sistema de riego automático funciona de la siguiente manera, cuando detecta que la humedad del suelo es baja y que el nivel de agua en el tanque es suficiente, activa el riego para la planta. Si no se cumplen estas condiciones, se activará una alarma para avisar al usuario de que el tanque no tiene agua suficiente. Dentro del tanque hay un motor de agua que se activa cuando ambas condiciones (humedad baja y nivel de agua alto) se cumplen. Además, un relé actúa como interruptor para controlar la bomba de agua. Este diseño asegura que las plantas se mantengan regadas adecuadamente y que el usuario sea notificado si falta agua en el tanque. La planta que utlizaremos se llama potus es una planta que requiere poca cantidad (50ml x Dia) lo que nos serviria como prueba para mirar cuanto dias demora el agua en el tanque de (6.623 ml). Tendremos 3 leds de color Verde, Amarillo y Rojo los cuales nos indicaran el nivel del agua verde significa que esta Lleno, el amarillo indica que esta medio y el rojo indica que esta vacio. Utlizaremos un modulo bluetooth para enviar los datos a otro disposivo para guardar los datos de la humedad y la cantidad de agua en n archivo y asi mostrar resultados.

COMPONENTES

Sensor de Humedad del Suelo

Sensor Ultrasonico (Medira el nivel de Agua)

Fuente De Poder (Fabricada en clase)

Motobomba

Microcontrolador (Arduino UNO)

Tres LEDS Indicadores (Verde, Amarillo, Rojo)

Rele

Buzzer

Modulo Bluetooth

Interrutor

Baquela PCB

Requisistos Funcionamiento:

La Humedad y el nivel se debe leer constantemente para un funcionamiento eficiente. Cuando la humedad sea baja y el nivel sea alto o medio activar la bomba y Regar la planta. Cuando el nivel de agua este en su nivel critico activa el buzzer y si detecta que no hay humedad que no active la bomba para evitar daños. Cada 60 mn envie los datos al dispositivo que esta conectado Actualmente. leds se activaran dependiendo del nivel si es alto (Verde) si es medio (Amarillo) si es bajo (Rojo).

Proceso de Ejecucion:

Entrada(s):

La variable (humedad) es para medir la humedad del suelo.

La variable (NivelAgua) es para medir el nivel del agua.

Proceso(s):

Hacer comparaciones de las medidas definidas. Activar/Desactivar la bomba segun las condiciones definidas.

Encender/Apagar los leds segun las condiciones definidas.

Activar/Desactivar el buzzer segun las condiciones definidas.

Enviar los datos de las medidas cada 30mn atravez del modulo Bluetooth.

Salidas(s):

Activacion/Desactivacion de la bomba.

Activacion/Desactivacion del buzzer.

Activacion/Desactivacion de los leds.

Enviar los datos.


Otras Variables:

La (Duracion) la utizamos para calcular la distancia que hay en el tanque y de alli pasa a la variable NivelAgua.

El (intervaloGuarda) lo utlizaremos para que cada 30 minutos enviar los datos por Bluetooth.

El (tiempoAnterior) lo utlizaremos para Almacenar el tiempo anterior para comparar con el tiempo actual.


Liberias:

Utlizaremos <SoftwareSerial.h> para conectarnos con el modulo bluetooth y asi enviar los datos a otro dispositivo.

WhatsApp Image 2024-05-22 at 9.34.55 AM.jpegObservaciones:

Que los componentes a utilizar sean compatibles con el Microcontrolador.

Utlizar un Lenguaje de programacion compatible con el Microcontrolador.

Hacer las conexiones en plataformas virtuales para probar y verificar que nuestro proyecto funcione en la vida real.

No superar el prosupuesto indicado 200.000 COP.

SISTESIS

Hoy en día, a muchas personas se les hace difícil estar pendientes de las plantas que tienen en su hogar debido a sus ocupaciones diarias. Como resultado, no siempre pueden regarlas a diario, y si las plantas no reciben agua regularmente, pueden morir. ¿Qué podemos hacer al respecto? Un sistema de riego automático que monitorea la humedad del suelo. Este sistema consta de una placa programable y varios sensores que permiten monitorear la humedad de la tierra. A través de operaciones automáticas, el sistema mantiene la planta bien regada, evitando que muera por falta de agua.

ANALISIS

PROBLEMA: Desarrollar un Sistema de riego Automatico que riegue una planta cuando la humedad de tierra sea baja y monitorear la cantidad de agua que hay en un dicho tanque y alertar al usuario cuando este en condicones criticas.

DETALLES: El sistema de riego automático funciona de la siguiente manera, cuando detecta que la humedad del suelo es baja y que el nivel de agua en el tanque es suficiente, activa el riego para la planta. Si no se cumplen estas condiciones, se activará una alarma para avisar al usuario de que el tanque no tiene agua suficiente. Dentro del tanque hay un motor de agua que se activa cuando ambas condiciones (humedad baja y nivel de agua alto) se cumplen. Además, un relé actúa como interruptor para controlar la bomba de agua. Este diseño asegura que las plantas se mantengan regadas adecuadamente y que el usuario sea notificado si falta agua en el tanque. La planta que utlizaremos se llama potus es una planta que requiere poca cantidad (50ml x Dia) lo que nos serviria como prueba para mirar cuanto dias demora el agua en el tanque de (6.623 ml). Tendremos 3 leds de color Verde, Amarillo y Rojo los cuales nos indicaran el nivel del agua verde significa que esta Lleno, el amarillo indica que esta medio y el rojo indica que esta vacio. Utlizaremos un modulo bluetooth para enviar los datos a otro disposivo para guardar los datos de la humedad y la cantidad de agua en n archivo y asi mostrar resultados.

COMPONENTES

Sensor de Humedad del Suelo
Sensor Ultrasonico (Medira el nivel de Agua)
Fuente De Poder (Fabricada en clase)
Motobomba
Microcontrolador (Arduino UNO)
Tres LEDS Indicadores (Verde, Amarillo, Rojo)
Rele
Buzzer
Modulo Bluetooth
Interrutor
Baquela PCB
Requisistos Funcionamiento:

La Humedad y el nivel se debe leer constantemente para un funcionamiento eficiente.
Cuando la humedad sea baja y el nivel sea alto o medio activar la bomba y Regar la planta.
Cuando el nivel de agua este en su nivel critico activa el buzzer y si detecta que no hay humedad que no active la bomba para evitar daños.
Cada 60 mn envie los datos al dispositivo que esta conectado Actualmente.
leds se activaran dependiendo del nivel si es alto (Verde) si es medio (Amarillo) si es bajo (Rojo).
Proceso de Ejecucion:

1. Entrada(s):

La variable (humedad) es para medir la humedad del suelo.
La variable (NivelAgua) es para medir el nivel del agua.

2. Proceso(s):

Hacer comparaciones de las medidas definidas.
Activar/Desactivar la bomba segun las condiciones definidas.
Encender/Apagar los leds segun las condiciones definidas.
Activar/Desactivar el buzzer segun las condiciones definidas.
Enviar los datos de las medidas cada 30mn atravez del modulo Bluetooth.

3. Salidas(s):

Activacion/Desactivacion de la bomba.
Activacion/Desactivacion del buzzer.
Activacion/Desactivacion de los leds.
Enviar los datos.
Otras Variables:

La (Duracion) la utizamos para calcular la distancia que hay en el tanque y de alli pasa a la variable NivelAgua.

El (intervaloGuarda) lo utlizaremos para que cada 30 minutos enviar los datos por Bluetooth.

El (tiempoAnterior) lo utlizaremos para Almacenar el tiempo anterior para comparar con el tiempo actual.


Liberias:

Utlizaremos <SoftwareSerial.h> para conectarnos con el modulo bluetooth y asi enviar los datos a otro dispositivo.

Observaciones:

Que los componentes a utilizar sean compatibles con el Microcontrolador.
Utlizar un Lenguaje de programacion compatible con el Microcontrolador.
Hacer las conexiones en plataformas virtuales para probar y verificar que nuestro proyecto funcione en la vida real.
No superar el prosupuesto indicado 200.000 COP.

