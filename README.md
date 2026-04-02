# Barajas-post1-u3
En el presente repositorio se presenta el desarrollo del laboratorio de la actividad postcontenido 1 de la unidad 3 "MANEJO DEL DEBUG". El laboratorio fue desarollado por Juan Carlos Barajas Quintero, con código 1152455. El propósito del laboratorio es aprender a configurar el entorno DOSBox en nuestros equipos, accediendo al depurador DEBUG, utilizando los comandos R, D, F, U y A para inspeccionar el estado inicial de los registros, rellenar y volcar bloques de memoria, y desensamblar y ensamblar código en memoria. Esta practica nos permite afianzar nuestros conocimientos de la arquitectura interna del PC por medio de la practica. 

COMENTARIOS SOBRE CADA CHECKPOINT:

CHECKPOINT 1:

PARTE A: En esta sección se realiza las configuraciones iniciales del entorno DOSBox. Previamente ya había creado una carpeta en mi disco C, denominada "DOSWork". Accediendo al emulador, use el comando MOUNT C C:\DOSWork para montar esta carpeta virtualmente como C dentro del emulador. Use los comandos  C:\> MD LAB3POS1
C:\> CD LAB3POS1 para cambiar a la carpeta específica de este laboratorio. El nombre de la carpeta no es "LAB3POST1" debido a que DOSBox indicaba que el tamaño máximo permitido es de 8 caracteres, y este nombre tenía 9 caracteres, superando esa cota máxima. 

PARTE B: Se hace uso del comando R para observar el estado previo de los registros. Se usa el comnado R AX para cambiar el valor del registro AX a 1234, y se vuelve a hacer uso de R para observar el cambio en el valor de este registro en específico. En mi caso, los registros de segmento apuntan al parrafo de memoria 0724. Esta sección permite entender que se puede alterar el valor de un registro en específico sin afectar a los demás. 

CHECKPOINT 2:

PARTE C: En esta sección, se ejecutó el comando F 200 L40 AB CD EF, que permite inicializar un rango de memoria con un patrón de bytes conocido. Después, se hizo uso del comando D 200 L40 para mostrar los bytes de la región recién inicializada en formato hexadecimal y ASCII. Finalmente hacemos uso del comando D 0 L20 para  explorar el área del PSP (que contiene información que el DOS prepara antes de ejecutar el programa). 

La salida del comando D se divide en tres secciones fundamentales: la dirección de memoria a la izquierda, el contenido hexadecimal al centro y la traducción ASCII a la derecha. La primera columna indica la ubicación exacta (segmento y desplazamiento) de los datos, mientras que el bloque central muestra 16 bytes de información pura por fila, usando un guion como separador visual. Finalmente, la sección de la derecha intenta interpretar esos bytes como texto legible, sustituyendo con puntos cualquier valor que no tenga una representación visual estándar. 

CHECKPOINT 3:

PARTE D: En esta última sección, se ejecutó primero el comando U 100 L10, que mostró el INT 20 del PSP seguido de bytes aleatorios de la memoria disponible. Posteriormente, se hizo uso del comando A 100 para escribir un programa simple de 4 instrucciones directamente en CS:0100. Se verificó el correcto ensamblaje del programa haciendo uso del comando U 100 109. Cabe aclarar que al ver el resultado de U, el byte resultante para la instrucción ADD AX,BX fue 01D8 y no 03C3, pero esto es debido que en la arquitectura del procesador 8086, muchas instrucciones se pueden escribir de dos formas válidas en lenguaje de máquina binario, dependiendo de cuál registro se considere el "origen" y cuál el "destino" en los bits internos. Así que esta diferencia fue debido a la forma en que se codificó el código de operación (Opcode) en el procesador x86, pero ambos son equivalentes y válidos. 
