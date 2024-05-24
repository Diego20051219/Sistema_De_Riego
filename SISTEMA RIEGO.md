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


Observaciones:

Que los componentes a utilizar sean compatibles con el Microcontrolador.

Utlizar un Lenguaje de programacion compatible con el Microcontrolador.

Hacer las conexiones en plataformas virtuales para probar y verificar que nuestro proyecto funcione en la vida real.

No superar el prosupuesto indicado 200.000 COP.


![image](https://github.com/Diego20051219/Sistema_De_Riego/assets/161365596/578b1c03-805e-46d4-baf9-2bdf128ce1e9)

DESARROLLO DEL ALGORITMO
PEUSOCODIGO

    Start

    Libreria <SoftwareSerial.h>
    Declare Integer SoftwareSerial BTSerial(2, 3)
    Constant Integer trig = 4
    Constant Integer echo = 5
    Constant Integer buzzer = 6
    Constant Integer humedad = A0
    Constant Integer bomba = 7
    Constant Integer verdePin = 8
    Constant Integer amarilloPin = 9
    Constant Integer rojoPin = 10
    Integer porcentajeNivelAgua = 0;
    Integer porcentajeHumedad = 0;
    Constant Long intervaloGuarda = 1000
    long tiempoAnterior = 0

    Module setup()
     Set pinMode(Humedad, INPUT)
     Set pinMode(trig, OUTPUT)
     Set pinMode(echo, INPUT)
     Set pinMode(bomba, OUTPUT)
     Set pinMode(buzzer, OUTPUT)
     Set pinMode(led_rojo, OUTPUT)
     Set pinMode(led_amarillo, OUTPUT)
     Set pinMode(led_verde, OUTPUT)
     Set Serial.begin(9600)
     Set BTSerial.begin(9600)

    End Module

    Module loop()
     Set humedad = analogRead(A0)
     Display ("La humedad: ")
     Display (porcentajeHumedad)
     Display ("%")
     Set porcentajeHumedad = map(lecturaSensor, 0, 1023, 100, 0)

     Set digitalWrite(trig, LOW);
     Set delayMicroseconds(2);
     Set digitalWrite(trig, HIGH);
     Set delayMicroseconds(10);
     Set digitalWrite(trig, LOW);
     Set duracion = pulseIn(echo, HIGH);
     Set NivelAgua = (duracion / 58);
     Display("El nivel de Agua: ");
     Display(porcentajeNivelAgua);
     Display(" %");
     set porcentajeNivelAgua = map(NivelAgua, 0, 12, 100, 0); 

    if (humedad >= 700 ) then
        if (NivelAgua <= 12)
          Set digitalWrite(bomba, LOW); // Enciende la bomba
          Set digitalWrite(buzzer, LOW);
          Set delay(2000); // Retraso de 2 segundos
          Set digitalWrite(bomba, HIGH);
        else
          Set digitalWrite(bomba,LOW); // Apaga la bomba
          Set digitalWrite(buzzer, HIGH);
          Set delay(2000); // Retraso de 2 segundos
          Set digitalWrite(buzzer, LOW);
        End if 
    else
     Set digitalWrite(bomba, LOW); // Apaga la bomba
     Set digitalWrite(buzzer, LOW);
    End if

    if (NivelAgua >= 12)
     Set digitalWrite(buzzer, HIGH);   
     Set delay(2000); // Retraso de 2 segundos
     Set digitalWrite(buzzer, LOW);
    End if

    if (NivelAgua >= 11 && NivelAgua >= 9)
       Set digitalWrite(led_rojo, HIGH);
       Set digitalWrite(led_amarillo, LOW);
       Set digitalWrite(led_verde, LOW);
    else if (NivelAgua <= 8 && NivelAgua >= 5) 
      Set digitalWrite(led_rojo, LOW);
      Set digitalWrite(led_amarillo, HIGH);
      Set digitalWrite(led_verde, LOW);
    else if (NivelAgua <= 4 && NivelAgua >= 0)
       Set digitalWrite(led_rojo, LOW);
       Set digitalWrite(led_amarillo, LOW);
       Set digitalWrite(led_verde, HIGH);
    else 
      Set digitalWrite(led_rojo, LOW);
      Set digitalWrite(led_amarillo, LOW);
      Set digitalWrite(led_verde, LOW);
    End if

    Set unsigned long tiempoActual = millis();
    if (tiempoActual - tiempoAnterior >= intervaloGuarda) 
      Set tiempoAnterior = tiempoActual;
      Set String datos = "La Humedad: " + String(porcentajeHumedad) + " %" + " | Nivel de Agua: " + String(porcentajeNivelAgua) + " %";
      BTSerial.Display(datos);
    End if

    if (BTSerial.available()) 
      Serial.write(BTSerial.read());
    End if

    if (Serial.available()) 
      Set BTSerial.write(Serial.read());
    End if 

    Delay(1000)
    End Module
    End

Componentes y Conexiones:

Arduino Uno: Plataforma de microcontrolador.

Módulo Bluetooth (HC-05/HC-06): Pines TX y RX conectados a los pines 2 y 3 del Arduino usando SoftwareSerial.

Sensor ultrasónico (HC-SR04): Pines trig (4) y echo (5).

Sensor de humedad del suelo: Conectado al pin analógico A0.

Bomba de agua: Controlada a través del pin digital 7 atravez de un Rele.

Buzzer: Conectado al pin digital 6.

LEDS indicadores:

Verde: Pin 8.
Amarillo: Pin 9.
Rojo: Pin 10.
Variables y Constantes:

SoftwareSerial BTSerial(2, 3): Inicialización de la comunicación serial con el módulo Bluetooth.

int trig, echo, buzzer, bomba, humedad, led_verde, led_amarillo, led_rojo: Pines utilizados.

long duracion, NivelAgua: Variables para la medición del nivel de agua.

const unsigned long intervaloGuarda = 1000: Intervalo de 1 segundo para enviar datos por Bluetooth.

unsigned long tiempoAnterior = 0: Almacenamiento del tiempo anterior para comparar con el tiempo actual.

Setup

La función setup( ) configura los pines como entrada o salida y establece la velocidad de comunicación serial con el ordenador y el módulo Bluetooth.

    void setup( ) {

    pinMode(humedad, INPUT);

    pinMode(trig, OUTPUT);

    pinMode(echo, INPUT);

    pinMode(bomba, OUTPUT);

    pinMode(buzzer, OUTPUT);

    pinMode(led_rojo, OUTPUT);
 
    pinMode(led_amarillo, OUTPUT);

    pinMode(led_verde, OUTPUT);

    Serial.begin(9600);

    BTSerial.begin(9600);

     }

Loop

La función loop( ) se ejecuta continuamente y contiene las siguientes funcionalidades:

Lectura de distancia con el sensor ultrasónico digitalWrite(trig, LOW);

La duración del pulso reflejado se convierte en una distancia.

Leer los datos de la variable echo.

En la variable NivelAgua Dividimos la duracion por 58 para asi obtener el nivel del agua en cm.


    void loop( ) {

    //Lectura de la humedad 

    humedad = analogRead(A0)
    Display ("La humedad: ")
    Display (porcentajeHumedad)
    Display ("%")
    porcentajeHumedad = map(lecturaSensor, 0, 1023, 100, 0)



    // Lectura de distancia con el sensor ultrasónico
    digitalWrite(trig, LOW);

     delayMicroseconds(2);

    digitalWrite(trig, HIGH);
    
    delayMicroseconds(10);
    
    digitalWrite(trig, LOW);

    duracion = pulseIn(echo, HIGH);

    NivelAgua = duracion / 58;

    Display("El nivel de Agua: ");

    Display(porcentajeNivelAgua);

    Display(" %");

    porcentajeNivelAgua = map(NivelAgua, 0, 12, 100, 0); 
Se leen constantente las varibles de humedad y del nivel del agua para un funcionamiento eficiente.
se utliza la funcion map para pasar eso valores a porcentaje y visualizarlos y entenderlos mejor.

Los valores del sensor de agua son en centimetros y van de 0 a 800cm indicamos que cuando la distancia sea 0 indique qu esta lleno y cuando sea >12 indique que esta vacio con el led rojo y el buzzer.

Los valores de humedad estan desde 1023 que la tierra esta totalmente seca y 0 que indica que esta humedad. Colocamos que cuando la humedad sea 1023 lo coloque en 100 % para indicar que la tierra esta totalmente seca 0 % que la tierra esta humeda.

    // Control de la bomba
     if (humedad >= 700 ) then
        if (NivelAgua <= 12)
          Set digitalWrite(bomba, LOW); // Enciende la bomba
          Set digitalWrite(buzzer, LOW);
          Set delay(2000); // Retraso de 2 segundos
          Set digitalWrite(bomba, HIGH);
        else
          Set digitalWrite(bomba,LOW); // Apaga la bomba
          Set digitalWrite(buzzer, HIGH);
          Set delay(2000); // Retraso de 2 segundos
          Set digitalWrite(buzzer, LOW);
        End if 
    else
     Set digitalWrite(bomba, LOW); // Apaga la bomba
     Set digitalWrite(buzzer, LOW);
    End if

    if (NivelAgua >= 12)
     Set digitalWrite(buzzer, HIGH);   
     Set delay(2000); // Retraso de 2 segundos
     Set digitalWrite(buzzer, LOW);
    End if
El funcionamiento de la activacion de la bomba consiste en que si la humedad del suelo es baja a un 40 % y el Nivel del agua es alto a un 85 % la bamba se activara para bombear la planta por 2 segundos ya que bombaria el agua seficiente a la planta cuando la humedad sea mayor que 70 % se desactiva.

El funcionamiento del buzzer es que se activa cuando el sensor de agua tiene un nivel de agua bajo ejemplo 10 % y para que no suene constante ya que es un sonido bastante agudo se retraso por 2 segundo.

    // LEDS indicaores

    if (NivelAgua >= 12 && NivelAgua >= 9)
       Set digitalWrite(led_rojo, HIGH);
       Set digitalWrite(led_amarillo, LOW);
       Set digitalWrite(led_verde, LOW);
    else if (NivelAgua <= 8 && NivelAgua >= 5) 
      Set digitalWrite(led_rojo, LOW);
      Set digitalWrite(led_amarillo, HIGH);
      Set digitalWrite(led_verde, LOW);
    else if (NivelAgua <= 4 && NivelAgua >= 0)
       Set digitalWrite(led_rojo, LOW);
       Set digitalWrite(led_amarillo, LOW);
       Set digitalWrite(led_verde, HIGH);
    else 
      Set digitalWrite(led_rojo, LOW);
      Set digitalWrite(led_amarillo, LOW);
      Set digitalWrite(led_verde, LOW);
    End if
    
Cada led se encendera dependiendo el valor del nivel del agua decimos que cuando el nivel sea 11 que se active el led rojo, 
cuando sea 8 o menor que se active el led amarillo, 
y cuando sea menor que 4 que se active el led verde. 
En cada condicion encedemos el que queremos y indicamos apagar los otros para que haya errores.

    // Envío de datos por Bluetooth cada intervalo definido 
     Set unsigned long tiempoActual = millis();
    if (tiempoActual - tiempoAnterior >= intervaloGuarda) 
      Set tiempoAnterior = tiempoActual;
      Set String datos = "La Humedad: " + String(porcentajeHumedad) + " %" + " | Nivel de Agua: " + String(porcentajeNivelAgua) + " %";
      BTSerial.Display(datos);
    End if

    if (BTSerial.available()) 
      Serial.write(BTSerial.read());
    End if

    if (Serial.available()) 
      Set BTSerial.write(Serial.read());
    End if 

    Delay(1000)
El modulo bluetooth envía datos de humedad del suelo y nivel de agua en porcentaje a través de Bluetooth cada intervalo definido. Además, permite la comunicación bidireccional entre el módulo Bluetooth y el puerto serie del Arduino, asegurando que los datos se actualicen y se transmitan en tiempo real. La función delay(1000) pausa la ejecución del código durante 1 segundo para evitar envíos constantes y excesivos de datos.
