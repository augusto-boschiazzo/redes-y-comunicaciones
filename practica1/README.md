# Practica 1

## Introducción

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


