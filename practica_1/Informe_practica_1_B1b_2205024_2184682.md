# Laboratorio de Comunicaciones
## Universidad Industrial de Santander

# Práctica 1

### Integrantes
- **OSCAR DANIEL CASTELLANOS MARIÑO** - 2205024
- **JUAN CAMILO GONZALEZ LEAL** - 2184682

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
07 de marzo de 2025

---
### PRACTICA 1A: GNU Radio para el procesamiento de señales
### Resumen
Durante la práctica, se demostró el teorema de Nyquist, que vincula la frecuencia de muestreo con la señal para evitar el aliasing. Se utilizaron señales senoidales y cuadradas para ejemplificar los efectos del muestreo. Con GNU Radio, se diseñaron diagramas de bloques para procesar señales de audio. Se resaltó la necesidad de que la frecuencia de muestreo sea al menos el doble del ancho de banda de la señal.

**Palabras clave:** GNU Radio, Nyquist, Aliasing.

### Introducción
#### Uso de bloque THROTTLE:
Este desempeña un papel crucial en el control del flujo de datos en GNU Radio. Su función principal radica en regular la velocidad de procesamiento de los datos en el sistema. Esto es esencial para evitar la saturación del sistema, garantizando un procesamiento eficiente y sin pérdidas. 
#### Bloque QT GUI Frequency SINK:
Este proporciona información visual sobre las frecuencias presentes en la señal en tiempo real. Este bloque genera un espectrograma en tiempo real que muestra la distribución de las frecuencias en la señal en función del tiempo.
- ¿Qué tan importante es la teoría de muestreo en el procesamiento de señales?
Esta tiene su importancia debido a que de esta manera se puede encontrar informacion en las señales, ya que una frecuencia de muestreo no ideal puede llevar a la perdida de información y generando aliasing, es por esto que se tiene que la frecuencia de muestreo debe ser al mas de dos veces la frecuencia de la señal, a una mayor frecuencia de muestreo se tiene mas información de la señal original aunque esto lleva a una cantidad de datos.
- El teorema de Nyquist y su relación con el ancho de banda
El Teorema de Nyquist establece que la frecuencia de muestreo debe ser al menos el doble de la frecuencia de la señal para evitar el solapamiento y la distorsión de la información. Además, el teorema señala que la tasa máxima de transmisión de información a través de un canal está limitada por el ancho de banda del canal y el ruido. Por lo tanto, si transmitimos una señal con un ancho de banda mayor al ancho de banda del canal, perderemos información en el proceso de transmisión.
- El aliasing
Se refiere a la presencia de componentes de frecuencia falsos en la señal muestreada, lo que afecta la claridad y fidelidad del sonido. En casos extremos, el audio puede perderse por completo debido a la incapacidad de reconstruir correctamente la señal original.
- ¿Cuándo es importante interpolar una señal?
Cuando se necesita adaptar la señal a un receptor o con una tasa de muestreo especifica, reducir el aliasing y tambien mejorar la precision de medidas en sistemas de control

### Procedimiento
Debe basarse en las acciones efectivamente realizadas durante el laboratorio, describiendo los procesos realizados y los resultados obtenidos. Para cada práctica se pueden brindar preguntas orientadoras o pasos a seguir para establecer lo que se espera lograr/estudiar/analizar/obtener/comparar. Por ejemplo:
- Describa los procesos realizados en el laboratorio  y los resultados obtenidos.

Durante el reconocimiento del entorno de trabajo de GNU Radio las primeras señales que se obtuvieron diferentes con cambios en su frecuencia fueron seno, coceno, diente de sierra, triangular y cuadrada, de las cuales de cada una se puede observar su componente de amplitud con respecto al tiempo, asi como su ganancia relativa medida en dB con respecto a la frecuencia medida en KHz mostrando de esta manera la ***magnitud del espectro de frecuencia***
| Tipo de señal | GNU Radio |
|-----------|-------|
| COSENO | <img src="parte_a/coseno1.png" width="300"> |
| SENO | <img src="parte_a/seno.png" width="300"> |
| DIENTE DE SIERRA | <img src="parte_a/sawtooth.png" width="300"> |
| CUADRADA | <img src="parte_a/square.png" width="300"> |
| TRIANGULAR | <img src="parte_a/triangle.png" width="300"> |

Diferentes variaciones en las señales

Para poder lograr una señal TRIANGULAR tipo flotante operando a una frecuencia de 4500 Hertz y amplitud 3, se tuvieron en cuenta los tipos de colores y sus datos correcpondientes para de esta manera identificando que, cuando el tipo de dato es ***Complex*** al trazarla en el dominio del tiempo, se nos muestra una componente real y una imaginaria, al tener el tipo de dato ***Float*** este solo nos muestra la componente real.

| Tipo de cambio en la señal | GNU Radio |
|-----------|-------|
| Señal seno operando a 100Hz, encontrando un pico en la respuesta de frecuencia en los 100Hz. | <img src="parte_a/seno_100hertz.png" width="300"> |
| Señal TRIANGULAR tipo flotante operando a una frecuencia de 4500 Hertz y amplitud 3 | <img src="parte_a/type_flotante.png" width="300"> |

El offset en una señal es un voltaje constante que se suma a la señal, ya sea positivo o negativo, vamos a ver como afecta a nuestras señales generadas mediante GNU Radio

| Señal con offset | GNU Radio |
|-----------|-------|
| Constate | <img src="parte_a/constant_offset.png" width="300"> |
| Coseno | <img src="parte_a/coseno_offset.png" width="300"> |
| Triangular | <img src="parte_a/triangle_offset.png" width="300"> |

Efectos sobre la forma de onda cuando se tiene una relación de muestreo

| Relación de muestreo | GNU Radio |
|-----------|-------|
| samp_rate/Frequency = 5 | <img src="parte_a/limite_=5.png" width="300"> <img src="parte_a/cmparacion=5.png" width="300">|
| samp_rate/frequency > 10 | <img src="parte_a/ny.png" width="300"> |

- ¿Cómo se alcanza el límite de Nyquist y que pasa cuando se disminuye de este?
Al alcanzar el limite se genera una disminucion en la informacion obtenida de la señal original, una vez se sigue disminuyendo la frecuencia de muestreo superando este limite se genera el aliasing lo cual hace que las frecuencias mas altas se reflejen en el espectro de frecuencias mas bajas.
- ¿Por qué al interpolar una señal en GNURADIO su frecuencia disminuye?
 Al interpolar una señal en GNURadio, se observa una disminución en su frecuencia debido al aumento en la tasa de muestreo. Este proceso expande el espectro de la señal y mejora su resolución en el dominio de la frecuencia, lo que resulta en una representación más detallada de la señal.
- ¿Por qué al diezmar una señal en GNURADIO su frecuencia aumenta?
Se observa un aumento en su frecuencia debido a la rediccion en la tasa de muestreo. Este proceso contrae el espectro de la señal y disminuyendo su resolución en el dominio de la frecuencia, lo que resulta en una representación menos detallada de la señal.
- ¿Cómo se puede determinar la frecuencia máxima de una señal desde lo experimental?
Para poder encontrar esta frecuencia maxima de una señal objetivo desde el laboratorio tenemos tanto el analizador de espectro como tambien osciloscopio digital, de los cuales podemos encontrar la frecuencia.
- Describa las funciones logradas con el Ecualizador desarrollado con GNURadio.
Experimentar con un ecualizador desarrollado con GNU Radio proporciona una comprensión profunda del funcionamiento de los filtros y sus efectos en la señal de audio. Permite ajustar y analizar las frecuencias de los filtros para observar cómo afectan a la señal de audio. Esto incluye la posibilidad de atenuar o realzar diferentes componentes de frecuencia, como voces o instrumentos musicales. Además, el ecualizador permite regular el volumen y explorar efectos de diezmado e interpolación en la señal. Esta experiencia práctica facilita el aprendizaje y la comprensión de los conceptos fundamentales del procesamiento de señales de audio.
### Conclusiones
Después de analizar el Teorema de Nyquist, se confirmó la importancia de respetar la frecuencia de muestreo adecuada para evitar pérdidas y distorsiones en una señal de audio. 
La visualización simultánea de las señales en el dominio del tiempo y la frecuencia facilitó la comprensión de los cambios producidos por los diferentes procesos y funciones aplicados, proporcionando una representación completa de la señal y sus características.
Se identificaron los efectos de interpolacion y diezmado, estos se pueden ejemplificar en señales de audio donde al momento de interpolar debido a la disminucion de la frecuencia la reproduccion del audio se relentiza, mientras que al diezmar la señal de audio esta se acelera debido al aumento en su frecuencia.
### Referencias
[1] Teorema de nyquist.” [Online]. Available:
https://techlib.net/techedu/teorema-de-nyquist/

[2]“Gnu radio.” [Online]. Available: 
https://wiki.gnuradio.org/index.php/Main_Page

### PRACTICA 1B: Reconociendo equipos
### Resumen
Se emplea un SDR (Software Defined Radio) como generador de señales y un osciloscopio para medir la amplitud de la señal transmitida, de esta manera se van a ir variando los valores de frecuencia y ganancia del transmisor para encontrar la amplitud medida experimentalmente con el osciloscopio en funcion de la amplitud dada desde al GNU Radio y respodiendo las preguntas **¿De que depende la precisión de medida en el osciloscopio?**, **Determine el porcentaje de amplitud de la señal recibida con respecto a la señal generada desde el PC**. Además, se estudia la atenuación en un cable coaxial RG58 A/U mediante un analizador de espectros, incorporando un atenuador de 30 dB

###Introducción

-De que depende la atenuacion de un cable
La atenuación en un cable coaxial se refiere a la disminución de la intensidad de la señal a medida que esta se propaga a lo largo del cable, por lo cual esta depende de la frecuencia de la señal transmitida, la longitud del cable cmo sus caracteristicas, el cable a utilizar durante la medicion de atenuacion en el laboratorio es el RG58 el cual cumple con tener perdidas minimas de intensidad para distancias menores a 15 metros.
-Un cable se puede considerar un filtro pasa-bajas
Este no se considera un filtro pasa bajas ya que su funcion no es filtrar las frecuencias de las señales, aunque este su puede atenuar las señales de frecuencias altas pudiento en ciertos casos comportarse como un filtro pasa bajas.


###Procedimiento

Una vez se a montado todos los bloques en el GNU Radio y conectandolos de manera tal que se pueda ganerar un buen funcionamiendo se procede a conectar el SDR al osciloscopio para que este pueda realizar las mediciones de amplitud que estamos necesitando, una vez todo se encuentre conectado de buena manera se procede a iniciar la simulación desde el GNU Radio para enviarle la informacion al SDR sobre la señal a generar, con esto se cambian los valores de Fc, GTX y amplitud generada obteniendo los datos y las imagenes de las siguientes tablas.
| FC = 200MHz | GTX = 10 | |
|-----------|-------|------------|
| *Amplitud generada* | *Amplitud medida en el osciloscopio* | *Señal observada* |
| 0.5 | 64 mV | <img src="parte_b/200_MHZ_gtx_10/Amplitud_0_5.jpg" width="300"> |
| 0.25 | 32.4 mV | <img src="parte_b/200_MHZ_gtx_10/Amplitud_0_25.jpg" width="300"> |
| 0.125 | 16.8 mV | <img src="parte_b/200_MHZ_gtx_10/Amplitud_0_125.jpg" width="300"> |
| 0.0625 | 8.5 mV | <img src="parte_b/200_MHZ_gtx_10/Amplitud_0_0625.jpg" width="300"> |


| FC = 300MHz | GTX = 20 | |
|-----------|-------|------------|
| *Amplitud generada* | *Amplitud medida en el osciloscopio* | *Señal observada* |
| 0.5 | 99.96 mV | <img src="parte_b/300_MHz_gtx_20/Amplitud_0_5.jpg" width="300"> |
| 0.25 | 49.02 mV | <img src="parte_b/300_MHz_gtx_20/Amplitud_0_25.jpg" width="300"> |
| 0.125 | 24.9 mV | <img src="parte_b/300_MHz_gtx_20/Amplitud_0_125.jpg" width="300"> |
| 0.0625 | 12.5 mV | <img src="parte_b/300_MHz_gtx_20/Amplitud_0_0625.jpg" width="300"> |


| FC = 400MHz | GTX = 30 | |
|-----------|-------|------------|
| *Amplitud generada* | *Amplitud medida en el osciloscopio* | *Señal observada* |
| 0.5 | 150.06 mV | <img src="parte_b/400_MHz_y_gtx_30/Amplitud_0_5.jpg" width="300"> |
| 0.25 | 83.4 mV | <img src="parte_b/400_MHz_y_gtx_30/Amplitud_0_25.jpg" width="300"> |
| 0.125 | 42.54 mV | <img src="parte_b/400_MHz_y_gtx_30/Amplitud_0_125.jpg" width="300"> |
| 0.0625 | 21.63 mV | <img src="parte_b/400_MHz_y_gtx_30/Amplitud_0_0625.jpg" width="300"> |

¿De que depende la precisión de medida en el osciloscopio?
La precision de la medida del osciloscopio depende del uso que se le de principalmente, saber como acomodar la señal, modelarla de modo que nosotros podamos identificar mejores datos y formas con los que podamos obtener informacion, por ejemplo para medir picos de tension es mas preciso hacerlo con los ejes que nos brinda el osciloscopio, y ya otros factores externos podrian ser la calidad del cable con la que se trasmite la señal, una correcta manipulacion de los equipos para conectarlos entre si.

Determine el porcentaje de amplitud de la señal recibida con respecto a la señal generada desde el PC.
El porcentaje de amplitud de la señal recibida es aproximadamente entre el 80% y 90% se pierde señal por medio de la transmision, conexiones etc. una forma de saber es usando la siguiente formula Porcentaje=((Amplitud en GNU RadioAm /plitud en osciloscopio​))×100 

Al momento de medir la atenuación de un cable coaxial RG58 A/U utilizando un SDR como generador de señales y un analizador de espectros como equipo de medición, se debe realizar la conexión del sistema asegurando que el SDR esté correctamente vinculado al analizador de espectros mediante el cable coaxial, además se debe incluir un atenuador de 30 dB en la conexión con el objetivo de evitar la saturación en la medición. Una vez conectados los equipos, se procede a configurar el analizador de espectros ajustando sus variables para poder observar cada uno de los cambios en la potencia.

| FC | GTX | Potencia entregada |
|-----------|-------|------------|
| 50 MHz | 6 | <img src="parte_b/Atenuacion_cable/50_MHz_y_GTX_6.jpg" width="300"> |
| 100 MHz | 6 | <img src="parte_b/Atenuacion_cable/100_MHz_y_GTX_6.jpg" width="300"> |
| 400 MHz | 27 | <img src="parte_b/Atenuacion_cable/400_MHz_y_GTX_27.jpg" width="300"> |
| 990 MHz | 18 | <img src="parte_b/Atenuacion_cable/990_MHz_y_GTX_18.jpg" width="300"> |


Se observa que la potencia recibida disminuye conforme aumenta la frecuencia de operación, lo que indica una mayor atenuación del cable a frecuencias más altas. Esto es evidente en la gráfica de "Potencia recibida", donde la potencia medida en el receptor disminuye progresivamente a medida que se incrementa la frecuencia.

La atenuación del cable, representada en la segunda gráfica, muestra un comportamiento creciente con la frecuencia. A frecuencias bajas, la atenuación es menor, mientras que a frecuencias altas, la atenuación es significativamente mayor, lo que sugiere una mayor pérdida en la transmisión de la señal a frecuencias más elevadas.

### Conclusiones
Durante el transcurso de esta practica se puedo evidenciar que la precisión de la medición en el osciloscopio depende de varios factores, incluyendo la resolución del equipo, la calibración de los canales, la correcta configuración de la escala vertical y horizontal, la calidad de las conexiones y la presencia de ruido en el sistema.

La relación entre la amplitud medida en el osciloscopio y la amplitud generada desde el PC varía dependiendo de la frecuencia de operación y la ganancia del transmisor. Si la atenuación no es constante en todas las mediciones, se puede atribuir a la pérdida en el cable coaxial, las características de propagación en el medio, la impedancia de los dispositivos conectados y posibles interferencias externas.

La atenuación del cable coaxial aumenta con la frecuencia, lo que indica mayores pérdidas de señal a frecuencias más altas.
### Referencias

[1]“Gnu radio.” [Online]. Available: 
https://wiki.gnuradio.org/index.php/Main_Page


### PRACTICA 1C: Mediciones de potencia y frecuencia

Objetivo General
Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Los estudiantes aprenderán a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.

### Actividad 1: Revisión de Especificaciones de los Equipos

Objetivo
Familiarizarse con las especificaciones técnicas de los equipos de laboratorio y entender cómo configurarlos para realizar mediciones.


¿Cuál es el rango de frecuencia del USRP 2920 y cómo se compara con el del analizador de espectros?

<img src="parte_c/Actividad_1/Analisador de espectro.jpg" width="300">
Rango de frecuencia del Analizador de Espectros R&S FPC1000:
El R&S FPC1000 cubre un rango de 5 Hz a 1 GHz. Este rango es más limitado que el del USRP 2920, pero es adecuado para aplicaciones de análisis de señales RF en el espectro inferior a media frecuencia.

| Componente | Rango de frecuencia | Rango de ganancia |
|-----------|-------|------------|
| Recepción (RX Frontend) | 68.750 MHz a 2200.000 MHz | Ganancia PGA0: 0.0 dB a 31.5 dB (paso de 0.5 dB) |
| Transmisión (TX Frontend) | 68.750 MHz a 2200.000 MHz | Ganancia PGA0: 0.0 dB a 31.0 dB (paso de 1.0 dB) |
| Recepción (RX Codec) | - | Ganancia Digital: 0.0 dB a 6.0 dB (paso de 0.5 dB) |

El USRP 2920 tiene un rango de frecuencia mayor que el analizador de espectros R&S FPC1000 (2.2 GHz frente a 1 GHz).
El USRP está diseñado para transmisión y recepción de señales, mientras que el analizador de espectros se enfoca en la medición y análisis de señales en un rango más específico.

¿Qué parámetros del USRP 2920 se deben configurar para transmitir una señal en una frecuencia específica?
Para transmitir una señal en una frecuencia específica con el USRP 2920, se deben configurar los siguientes parámetros:
*Frecuencia de transmisión (TX Frequency)*
*Ancho de banda de muestreo (Sampling Rate)*
*Amplitud de la señal*
*Modulación*
*Ganancia de transmisión (TX Gain)*


¿Cómo se configura el osciloscopio para medir la amplitud y la frecuencia de una señal?

Para medir la amplitud y la frecuencia de una señal en un osciloscopio, primero conecta la señal al canal de entrada para luego justar la base de tiempo (Time Base) para visualizar al menos un ciclo completo de la señal, modificando el tiempo por división en el eje horizontal, se ajusta la escala de voltaje (Vertical Scale) para que la amplitud sea claramente visible. 
Para medir la frecuencia, puedes contar los ciclos completos en la pantalla y multiplicarlos por la frecuencia de la base de tiempo, o usar las herramientas automáticas del osciloscopio, la amplitud se observa la diferencia entre el valor máximo y mínimo en el eje vertical, utilizando la medición de pico a pico proporcionada por el equipo.

¿Qué diferencia hay entre medir una señal en el dominio del tiempo (osciloscopio) y en el dominio de la frecuencia (analizador de espectros)?

| Medicion | - |
|-----------|-------|
| Dominio del tiempo (Osciloscopio) | Mide como varia una señal en el tiempo, es útil para observar las formas de onda de señales, ver transitorios y estudiar cómo cambian las señales. |
| Dominio de la frecuencia (Analizador de espectros) | Mide cómo se distribuyen las frecuencias en una señal, es útil para ver las frecuencias dominantes en una señal, detectar distorsión armónica, medir la potencia en diferentes bandas de frecuencia y analizar la ocupación del espectro. |

¿Cómo se mide el piso de ruido en el analizador de espectros? ¿Cómo afecta la frecuencia central, SPAN y RBW la medida de piso de ruido? ¿Por qué?

Evidencia

Lista con las 5 especificaciones más relevantes de cada equipo.

| Equipo | Especificaciones |
|-----------|-------|
| USRP 2920 | Frecuencia de operación: 50 MHz a 2.2 GHz. Ancho de banda de muestreo: 25 MS/s. Modulación: Soporta modulación digital y analógica. Conectividad: Dos puertos de RF (entradas/salidas) con conectores SMA. Interfaz: Conexión USB 3.0 para la transferencia de datos entre el dispositivo y un PC, compatible con plataformas como GNU Radio. |
| Osciloscopio R&S RTB2004 | Frecuencia de muestreo: 2 Gsample/s. Ancho de banda: 70 MHz. Pantalla: Pantalla táctil capacitiva de 10,1 pulgadas. Canales: 4 canales analógicos. Profundidad de memoria: Hasta 10 Mpts por canal. |
| Analizador de Espectros R&S FPC1000 | Rango de frecuencia: 5 Hz a 1 GHz. Análisis en tiempo real: Capacidad para realizar análisis de espectro en tiempo real y visualizar el espectro de señales. Resolución de ancho de banda: Ancho de banda de resolución de 1 Hz. Sensibilidad de la señal: Rango de detección de -150 dBm. Pantalla: Pantalla de 7 pulgadas a color. |

Se realizó la mediciones de piso ruido, quedando como evidencia las siguientes imagenes

<img src="parte_c/Actividad_1/Ruido de piso.jpg" width="300">
<img src="parte_c/Actividad_1/rp.jpg" width="300">


### Actividad 2: Simulación de Señales en GNU Radio

### **Objetivo**
Generar y analizar señales en GNU Radio para entender cómo se comportan diferentes formas de onda en tiempo y frecuencia.

### **Procedimiento**

  
1. **Análisis de Señales** 
   - Analice y valide los resultados en el dominio del tiempo y de frecuencia si se modifica:
     
***El tipo de dato de la fuente (compleja o flotante)***
  
 Cuando se tiene el tipo de dato en *float* lo que se logra es generar una señal real sin componente imaginaria, por lo cual en el dominio del tiempo solo se observa una senosoidal y en el dominio de la frecuencia se observa un solo pico.

Al tener el tipo de dato en *complex*, en el dominio del tiempo se pueden observar dos señales las cuales corresponden a la parte real e imaginaria de la misma y en el dominio de la frecuencia, se pueden observar dos picos debido a la modulacion en frecuencia.

***la forma de onda***

Al cambiar la forma de onda en el dominio del tiempo se nota cual es el tipo esperado, en el dominio de la frecuencia para los tipos de senales se observan sus armonicos.

***la frecuencia, fase de la señal y amplitud***
| | |
|-----|------|
| Frecuencia | Al cambia esta en el tiempo se observa como se repite mas veces, en la frecuencia los picos se desplazan hacia la frecuencia que se esta utilizando |
| Fase | Cambia el punto de inicio de la onda |
| Amplitud | En el tiempo varia la amplitud de la señal mientras que en la frecuencia la altura del pico aumentara o disminuira dependiendo de la misma |

   - Modifique el nivel de ruido del modelo de canal y analice el efecto en tiempo y frecuencia.

Para la señal en el dominio del tiempo se observa como esta comienza a tener una mayor dispersion oscilacion al ir aumentando el ruido, cosa que nos esta aumentando la relacion señal a ruido, ahora en el dominio del tiempo lo que se produce es un aumento en el piso de ruido lo que hace que la señal sea menos definida.

Acontinuacion se muestran las imagenes tomadas en el laboratorio.

| Tipo | Simulacion |
|-----|------|
| Compleja | <img src="parte_c/Actividad_2/compleja.jpg" width="300"> |
| Flotante | <img src="parte_c/Actividad_2/flotante.jpg" width="300"> |
| Compleja con offset | <img src="parte_c/Actividad_2/compleja_con_offset.jpg" width="300"> |
| Compleja con offset y cambio de frecuencia | <img src="parte_c/Actividad_2/compleja_variando_frecuencia_offset.jpg" width="300"> |
| Compleja sin offset y cambio de frecuencia | <img src="parte_c/Actividad_2/5_Aumento_frecuencia_sin_offset.jpg" width="300"> |
| Añadiendo ruido a una señal compleja | <img src="parte_c/Actividad_2/6_añadiendo_ruido_compleja.jpg" width="300"> |
| Añadiendo ruido a una señal flotante | <img src="parte_c/Actividad_2/8_flotante_con_ruido.jpg" width="300"> |
| Compleja con ruido y cambio de fase | <img src="parte_c/Actividad_2/9_compleja_ruido_carrier_cambio_de_fase.jpg" width="300"> |
| Compleja con aumento de amplitud | <img src="parte_c/Actividad_2/10_compleja_amplituda_cambiada_fase_ruido_carrier.jpg" width="300"> |
| Compleja menor amplitud y ruido | <img src="parte_c/Actividad_2/11_compleja_menor_amplitud_ruido_fase_carrier_frecuencia.jpg" width="300"> |
| Flotante con cambio de amplitud | <img src="parte_c/Actividad_2/12_flotante_amplitud_0.4.jpg" width="300"> |
| Seno con ruido | <img src="parte_c/Actividad_2/13_seno.jpg" width="300"> |
| Cuadrada | <img src="parte_c/Actividad_2/14_cuadrada.jpg" width="300"> |

### **Preguntas Orientadoras**
1. ¿Cómo se puede explicar matemáticamente la diferencia entre una fuente de tipo flotante y una de tipo complejo?

| Matematicamente | |
|---|---|
| Float | s(t) = A \cos(2\pi f t + \phi) |
| Complex | s(t) = A \cos(2\pi f t + \phi) + j A \sin(2\pi f t + \phi) |
   
3. ¿Cómo afecta la forma de onda a la distribución de energía (potencia) en el dominio de la frecuencia?

Para una senosoidal toda la energia se concentra en una sola frecuencia observando de esta manera en espectro un solo pico.
Una señal cuadrada y triangular en el dominio de la frecuencia aparecen armonico.
   
5. ¿Qué sucede con la señal en el dominio del tiempo y la frecuencia si se modifican los diferentes parámetros de la fuente? ¿Lo observado corresponde a lo esperado teóricamente?

| Se modifican los parametros | |
|---|---|
| Frecuencia | En el tiempo aumentan la cantidad de ciclos y en el dom. freq. se desplaza el pico del espectro a la nueva frecuencia |
| Fase | En el tiempo cambia la posicion sin cambiar la forma de onda y en la frecuencia solo cambia su fase mas no su magnitud |
| Amplitud | En el tiempo cambia su tamaño y en la frecuencia su potencia espectral crecen proporcionalmente a A^2 |

7. ¿Qué diferencias se observan entre una señal senoidal y una señal cuadrada en el dominio de la frecuencia?

| Caracteristica | Señal senoidal | Señal cuadrada |
|---|---|---|
| Dominio del tiempo  | Onda suave y continua  | Onda con transiciones abruptas  |
| Dominio de la frecuencia  | Un solo pico en *f*  | Pico en *f* y armonicos impares en *3f*, *5f*, *7f*...  |
| Contenido espectral  | Energia concentrada en una frecuencia  | Energia distribuida en multiples frecuencias  |
| Aplicaciones  | Modulacion de señales  | Electronica digital  |


## **Actividad 3: Transmisión y Medición de Señales con el USRP 2920**

### **Objetivo**
Transmitir señales usando el USRP 2920 y medir parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### **Procedimiento**
1. **Configurar el USRP 2920**:
   - Configure el flujograma en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presionando `E` (enable) o `D` (disable), respectivamente.
   - Identifique el bloque de frecuencia de muestreo (samp_rate) y observe el efecto de cambiar su valor (e.g. 10 kHz).
   - Configure la frecuencia de muestreo (samp_rate) en 1 MHz.
   - Verifique el efecto de modificar la frecuencia y ganancia del USRP. 

Se realiza la configuracion dandonos como resultado la evidencia:

| | |
|---|---|
| ganancia_a_10dB | <img src="parte_c/Actividad_3/1_configuracion/ganancia_a_10dB.jpg" width="300"> |
| ganancia_a_10dB_samp_rate_1MHz | <img src="parte_c/Actividad_3/1_configuracion/ganancia_a_10dB_samp_rate_1MHz.jpg" width="300"> |
| original_2000Hz | <img src="parte_c/Actividad_3/1_configuracion/original_2000Hz.jpg" width="300"> |
| original_a_1000Hz | <img src="parte_c/Actividad_3/1_configuracion/original_a_1000Hz.jpg" width="300"> |
| samp_rate_a_1MHz | <img src="parte_c/Actividad_3/1_configuracion/samp_rate_a_1MHz.jpg" width="300"> |



2. **Medición con el Analizador de Espectros**:


   - Mida el piso de ruido normalizado a la frecuencia de portadora que va a utilizar.
  
| Piso de ruido | |
|---|---|
| Medicion piso ruido 800MHz | <img src="parte_c/Actividad_3/2_pisoruido/1_medir_pisoruido_800MHz_aprox_6dB.jpg" width="300"> |
| Medicion piso de ruido ref -20 | <img src="parte_c/Actividad_3/2_pisoruido/2_pisoruido_ref-20_en_simulador_0.jpg" width="300"> |
| Piso de ruido minimo | <img src="parte_c/Actividad_3/2_pisoruido/3_pisoruido_minimo.jpg" width="300"> |
| Medicion piso ruido maximo | <img src="parte_c/Actividad_3/2_pisoruido/4_pisoruido_maximo.jpg" width="300"> |
| Piso de ruido normalizado | <img src="parte_c/Actividad_3/2_pisoruido/5_pisoruido_normalizado.jpg" width="300"> |


     
   - Analice y valide los resultados en el dominio de la frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.

<img src="parte_c/Actividad_3/3_variaciones/1.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/2.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/3.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/4.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/5.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/6.jpg" width="300">
<img src="parte_c/Actividad_3/3_variaciones/7.jpg" width="300">
  
 
   - Mida potencia de la señal transmitida y ancho de banda de diferentes señales generadas.
   - Conecte una antena apropiada a la entrada del analizador de espectros y observe el espectro de una señal FM (las estaciones FM se sitúan entre los 88 MHz y 108 MHz). Mida su ancho de banda y relación señal a ruido. 
   - Determinar la máxima potencia de transmisión.

| | |
|---|---|
| ampliando_freq_muestreo | <img src="parte_c/Actividad_3/4_med_potencia/ampliando_freq_muestreo.jpg" width="300"> |
| con_antena | <img src="parte_c/Actividad_3/4_med_potencia/con_antena.jpg" width="300"> |
| sin_antena | <img src="parte_c/Actividad_3/4_med_potencia/sin_antena.jpg" width="300"> |
| sintonizando | <img src="parte_c/Actividad_3/4_med_potencia/sintonizando.jpg" width="300"> |
| sintonizando_frecuencia | <img src="parte_c/Actividad_3/4_med_potencia/sintonizando_frecuencia.jpg" width="300"> |
| transmicion | <img src="parte_c/Actividad_3/4_med_potencia/transmicion.jpg" width="300"> |


   - Evalúe la respuesta en frecuencia del canal midiendo los cambios de ganancia del sistema cuando varía la frecuencia de portadora.

<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/1.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/2.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/3.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/4.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/5.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/6.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/7.jpg" width="300">
<img src="parte_c/Actividad_3/5_respuesta en frecuencia del canal/8.jpg" width="300">

4. **Medición con el Osciloscopio**:

<img src="parte_c/Actividad_3/6_medidas de osciloscopio/1.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/2.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/3.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/4.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/5.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/6.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/7.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/8.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/9.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/10.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/11.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/12.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/13.jpg" width="300">
<img src="parte_c/Actividad_3/6_medidas de osciloscopio/14.jpg" width="300">



### **Preguntas Orientadoras**
1. ¿Cómo se configura el USRP 2920 para transmitir una señal en una frecuencia específica?

Para configurar el USRP 2920 y transmitir una señal en una frecuencia específica, es necesario ajustar varios parámetros clave en GNU Radio. Primero, se debe establecer la frecuencia central, que define la frecuencia portadora de la señal a transmitir, luego se configura la ganancia de transmisión, que ajusta la potencia de salida del USRP.

2. ¿Qué parámetros del flujograma afectan la potencia de la señal transmitida?

Uno de los más importantes es la ganancia de transmisión, que controla el nivel de amplificación aplicado a la señal antes de su transmisión. Otro parámetro relevante es la amplitud de la señal baseband generada en el software, ya que señales de mayor amplitud producirán una mayor potencia de transmisión.

3. ¿Cómo se mide el ancho de banda de la señal transmitida en el analizador de espectros?

se establece la frecuencia central en la misma frecuencia de transmisión del USRP, se ajusta el SPAN (ancho de frecuencia visible) para asegurarse de que toda la señal quede dentro de la pantalla del analizador. Un parámetro clave es la RBW (Resolution Bandwidth), que determina la resolución espectral de la medición.

4. ¿Qué diferencias se observan en las mediciones de potencia cuando se varía la ganancia del USRP?

Al aumentar la ganancia de transmisión en el USRP, la potencia de la señal medida en el analizador de espectros también aumenta proporcionalmente. Sin embargo, si la ganancia es demasiado alta, pueden aparecer efectos no deseados como distorsión no lineal y saturación del amplificador, lo que genera armónicos y productos de intermodulación en el espectro.

5. ¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?

Sí, es posible estimar la potencia de una señal utilizando un osciloscopio, pero con ciertas limitaciones. La potencia puede calcularse a partir del voltaje pico a pico o voltaje RMS medido en la pantalla del osciloscopio y la impedancia del sistema

## **Actividad 4: Análisis de Resultados y Conclusiones**

### **Objetivo**
Analizar los resultados obtenidos y sacar conclusiones sobre el comportamiento de las señales en diferentes condiciones para elaborar el informe.

### **Preguntas Orientadoras**
1. ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?

La potencia de la señal juega un papel crucial en la calidad de la comunicación, ya que determina la relación señal a ruido (SNR) y, por lo tanto, la capacidad del receptor para detectar e interpretar la información transmitida.

2. ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?

Si una señal tiene una potencia cercana o inferior al piso de ruido, será difícil de detectar, ya que se mezclará con el ruido de fondo, un piso de ruido bajo permite detectar señales más débiles con mayor precisión, mientras que un piso de ruido alto limita la sensibilidad del receptor y reduce la capacidad de recibir señales de baja potencia sin errores.

3. ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?

Los equipos de medición como osciloscopios, analizadores de espectros y radios definidas por software (SDR) tienen limitaciones en ancho de banda y precisión.

4. ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?

Una opción es reducir el ancho de banda de resolución (RBW) en un analizador de espectros, lo que permite una mejor discriminación de señales débiles, se pueden utilizar filtros pasa-banda para eliminar componentes de ruido fuera de la banda de interés. 

5. ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?

En telecomunicaciones, permite ajustar la potencia de transmisión para cumplir con regulaciones y evitar interferencias. En radiofrecuencia, es clave para evaluar la ocupación del espectro y optimizar el uso de bandas. En sistemas inalámbricos, ayuda a garantizar la calidad del servicio ajustando el ancho de banda de transmisión según las condiciones del canal.

6. ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?

La respuesta en frecuencia de un canal alámbrico se puede medir inyectando una señal de barrido de frecuencia (sweep) en la entrada del canal y analizando la señal recibida en la salida, esto se puede hacer con un analizador de redes o con un generador de señales y un analizador de espectros, la diferencia en amplitud y fase entre la señal transmitida y la recibida en función de la frecuencia proporciona la respuesta del canal.




