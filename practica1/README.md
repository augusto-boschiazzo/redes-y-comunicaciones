# Practica 1

### Introducción

---

1. _¿Qué es una red? ¿Cuál es el principal objetivo para construir una red?_

   Una red es un sistema de computadoras interconectadas, con el fin de comunicar información entre ellas. Se pueden conectar a través de distintos sistemas, como cables, WiFi, bluetooth, señal satelital, entre otros.

---

2. _¿Qué es Internet? Describa los principales componentes que permiten su funcionamiento._

   El Internet es una red pública, compuesta por **hosts** o **end systems**, que producen y consumen información. A su vez, están conectados por **enlaces de comunciación** y **conmutadores de paquetes**. Los conmutadores de paquetes más comunes son los **routers** y los **conmutadores de capa de enlace**. 

   Los end systems acceden al internet a través de los ISP o **Internet Service Providers**, que se clasifican en residenciales, corporativos, universitarios, públicos (hoteles, aeropuertos, cafeterías), y de datos celulares.

   Estos ISP de menor nivel se conectan con los de mayor nivel (nacionales e internacionales).

   Los distintos componentes del Internet se conectan y comunican usando protocolos, como el TCP, el IP, entre otros.

---

3. _¿Qué son las RFCs?_

   Las RFCs (**request for comments** o **requiere comentarios**), son documentos para definir estándares. Iniciaron como requerimientos de comentarios acerca de cómo resolver problemas de diseños de protocolos y redes.

---

4. _¿Qué es un protocolo?_

   Un protocolo define las reglas y la forma de comunicación entre dispositivos de una red. Establece el formato y el orden de los mensajes, y las respuestas específicas al recibir estos mensajes o ante eventos posibles.

---

5. _¿Por qué dos máquinas con distintos sistemas operativos pueden formar parte de una misma red?_

   Se pueden conectar cualquier tipo de dispositivo a una misma red siempre que tengan interfaces adecuadas para la conexión. En cuanto a su comunicación, siempre y cuando usen los protocolos establecidos, cualquier tipo de dispositivo se puede comunicar en una red usándolos. Este es el problema que buscaban resolver los RFCs.

---

6. _¿Cuales son las dos categorías en las que pueden clasificarse los sistemas finales o end systems? Dé un ejemplo del rol de cada uno en alguna aplicación distribuida que corra sobre Internet._

   Los sistemas finales o end systems se pueden clasificar en **clientes** y **servidores**. Los clientes suelen ser computadoras de escritorio, laptops, smartphones, y otros dispositivos que consumen información, mientras que los servidores son computadoras de alta capacidad que **sirven** páginas, stream de video, envío de emails, entre otras. En general, estos servidores se encuentran en **datacenters**.

---

7. _¿Cuál es la diferencia entre una red conmutada de paquetes y una red conmutada de circuitos?_

   La diferencia entre ambos tipos de red está en el uso de los recursos de comunicación. En una red conmutada de circuitos, los recursos se reservan por la duración del enlace, y la información se envía de manera constante. En cambio, en la red conmutada de paquetes, los recursos se usan _on demand_, y cuando se quieren utilizar se deben encolar y esperar a su turno. 

---

8. _Analice qué tipo de red es una red de telefonía y qué tipo de red es Internet_

   Las redes tradicionales de teléfono son redes conmutadas de circuitos, ya que se necesita enviar los datos de manera constante en la duración de una llamada. Esto implica que una conexión reservará los recursos necesarios para la comunicación, y si se terminan los recursos, no se podrá crear otra conexión hasta que terminen las anteriores. A su vez, los dispositivos telefónicos sólo tendrán una conexión activa a la vez.

   El Internet es una red conmutada de paquetes. Esto implica que se puedan realizar múltiples conexiones a la vez usando los mismos recursos, y cada conexión esperará su turno para usarlo. Esto permite también que un dispositivo tenga varias conexiones a la vez, permitiendo que múltiples aplicaciones accedan a su propia conexión.

---

9. _Describa brevemente las distintas alternativas que conoce para acceder a Internet en su hogar._

   Desde mi hogar, puedo acceder al internet mediante mi router, ya sea por cable Ethernet directamente conectado o desde WiFi. También usando datos celulares, usando antenas celulares. 

   Ambos medios se conectan a un ISP, que se comunica con otros ISP para servir el contenido de distintos lugares del mundo.

---

10. _¿Qué ventajas tiene una implementación basada en capas o niveles?_

    Una implementación basada en capas permite organizar un sistema complejo, de manera tal que cada capa ofrece servicio a la capa superior, y accede a los servicios de la capa inferior, dando lugar a modularización.

    Además permite que se usen distintos protocolos por capa, dando lugar a un sistema en el que tanto el cliente como el servidor pasan por las mismas capas, y cada una de ellas usa el mismo protocolo en una computadora que en la otra.

---

11. _¿Cómo se llama la PDU de las capas de Aplicación, Transporte, Red y Enlace?_

    Las distintas PDU (**Protocol Data Unit**) para las capas son:
     *Aplicación (Mensaje): Es el paquete de información que envía una aplicación de un end system a la aplicación de otro.
     *Transporte (Segmento): El mensaje se divide en partes y es enviado usando el protocolo TCP o UDP de Internet.
     *Red (Datagrama): La capa de transporte envía un segmento con una dirección, y la capa de red se encarga de encontrar el destino. Se usa el protocolo IP.
     *Enlace (Frame): Los datagramas se enviarán a través de varios nodos de enlace antes de alcanzar el destino. En cada uno de ellos, puede usar distintos protocolos de capa de enlace, por ejemplo, de un enlace a otro puede usar Ethernet, y luego PPP (Punto a punto).

---

12. _¿Qué es la encapsulación? Si una caparealiza la encapsulación de datos, ¿qué capa del nodo receptor realizará el proceso inverso?_

    La encapsulación de datos es el proceso por el cual cada capa organiza el mensaje agregando información adicional, ya sea para la capa inferior como para la misma capa al otro lado de la conexión. 

    Este proceso permite la comunicación entrees el proceso por el cual cada capa organiza el mensaje agregando información adicional, ya sea para la capa inferior como para la misma capa al otro lado de la conexión. Este proceso permite la comunicación entre las capas de los distintos dispositivos.

    Siempre que se realiza una encapsulación, el proceso inverso lo realizará la misma capa del dispositivo que recibe la comunicación.

---

13. _Describa cuales son las funciones de cada una de las capas del stack TCP/IP o protocolo de Internet._

    Las capas del protocolo TCP/IP son las capas de aplicación, transporte, red, enlace y física, aunque en ocasiones se agrupan a la capa de enlace y la física para simplificar.

    La capa de aplicación se encarga de representar datos, recibirlos o producirlos, y enviar mensajes a destinatarios de otros end systems.

    La capa de transporte realiza la comunicación de mensajes de la capa de aplicación de distintos endpoints. En el internet existen dos protocolos de transporte: **TCP** y **UDP**.

    La capa de red envía los segmentos a la capa de transporte de otro host. La capa de red del Internet tiene protocolos que indican la ruta que debe seguir el mensaje para llegar al destino.

    La capa de enlace permite enviar la información de un nodo al siguiente. Incluye protocolos como Ethernet, WiFi, PPP, entre otros.

    La capa física mueve los datos entre los nodos de a bits. Existen distintos medios de transmisión, como los cables coaxiales, fibra óptica, entre otros.

---

14. _Compare el modelo OSI con la implementación TCP/IP_

    El modelo OSI es un modelo teórico creado por la ISO en 1984. Consta de 7 capas: Aplicación, presentación, sesión, transporte, red, enlace y física.
    
    Respecto del modelo TCP/IP, agrega las capas de presentación y de sesión. El modelo TCP/IP es el usado por el Internet para acceder a la Web, por el uso de sus protocolos, ya que TCP por ejemplo engloba las tres capas más altas del modelo OSI, ya que envía y formatea los datos para su envío, además de encargarse de mantener la sesión de la conexión.
