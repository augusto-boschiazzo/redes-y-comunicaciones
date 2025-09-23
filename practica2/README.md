# Practica 2

### Capa de Aplicación - HTTP

---

1. _¿Cuál es la función de la capa de aplicación?_

   La capa de aplicación está compuesta de servicios de comunicación a los usuarios, User Interfaces, aplicaciones construidas sobre la red, y protocolos de comunicación como HTTP, SMTP, etc. 

   La función de la capa de aplicación varía según el end system: el cliente hace peticiones y presenta las respuestas, el servidor recibe peticiones, las procesa y responde.

   La capa de aplicación se encuentra presente sólo en los end systems, no en links y switches, que sólo tienen la capa de red y sus capas inferiores para poder direccionar los mensajes.

---

2. _Si dos procesos deben comunicarse:_

    1. _¿Cómo podrían hacerlo si están en distintas máquinas?_

       La forma en la que se pueden comunicar dos procesos de distintas máquinas es a través de una interfaz de software llamada **socket**. 

       Cuando un proceso se quiere comunicar con el proceso de otra máquina, debe conocer su IP, para saber a dónde enviar los mensajes. Pero también debe conocer el **número de puerto**, que indica al socket de qué proceso enviar la información.

    2. _Y si están en la misma, ¿qué alternativas existen?_

        * Modelo de mainframe centralizado: el cliente solo corre la comunicación y la interfaz de usuario, mientras que el servidor realiza todo el resto de operaciones.
        * Concurrencia: Varios procesos pueden comunicarse en una misma computadora.

---

3. _Explique brevemente el modelo cliente/servidor. Dé un ejemplo de cliente/servidor en la vida cotidiana y un ejemplo de un sistemam informático. ¿Conoce algún otro modelo de comunicación?_

   El modelo cliente/servidor indica que existen hosts clientes, que hacen requisitos a otro host servidor, que los recibe y da respuestas. El servidor siempre está disponible, y tiene una IP fija, por lo que siempre es accesible para los clientes.

   En los sistemas informáticos, las páginas web son un ejemplo del modelo, ya que siempre son accesibles, y tienen una IP siempre conocida a la que se puede acceder en cualquier momento.

   Otros modelos son el modelo **Mainframe** y el modelo **P2P** o peer to peer. En el modelo P2P ambos hosts son considerados pares, y se considera cliente al que hace el requerimiento y servidor al que lo provee, pero un cliente puede también proveer en cualquier momento a otro host, considerándose así como servidor.

---

4. _Describa la funcionalidad de la entidad genérica "Agente de Usuario" o "User Agent"._

   La funcionalidad del header HTTP User Agent, que representa el **navegador** desde el que el cliente hace la request, es la de permitir al servidor enviar distintas versiones del mismo objeto si fuera necesario.

---

5. _¿Qué son y en qué se diferencian HTML y HTTP?_

   HTML (**HyperText Markup Language**) es un lenguaje de programación que permite diseñar páginas web usando elementos programados en los navegadores. Se pensó como un lenguaje que emulara la estructura de los diarios.

   HTTP (**HyperText Transfer Protocol**) es un protocolo de la capa de aplicación creado para compartir archivos HTML a través de la web. Está compuesto del archivo requerido, la versión del protocolo usada, un código de respuesta o un método de requisito, headers y el cuerpo de la respuesta con la información requerida.

---

6. _HTTP tiene definido un mensaje para request y response._

    1. _¿Qué información de la capa de aplicación nos indica si un mensaje es de request o response para HTTP? ¿Cómo está compuesta dicha información? ¿Para qué sirven las cabeceras?_
       
       La forma de darse cuenta si un mensaje HTTP es request o response es mirando a la primera línea. En el caso de las requests, la primera línea se conoce como **request line**, y contiene el método usado en la request (**GET**, **POST**, **HEAD**, etc). En el caso de las responses, la primera línea se llama **status line**, y contiene un código que indica el estado de la respuesta (200 indica success, 404 indica que no se encontró el recurso requerido, etc.

       Las cabeceras dan información adicional al host destino, como el User Agent, que indica el programa usado por el cliente para hacer el requisito, el **host**, que permite pedir un recurso específico de un servidor sin la necesidad de indicar la totalidad de la URL en la request line, **Accept Language**, que indica el lenguaje esperado por el cliente (español, inglés, francés, etc), entre otros headers.

    2. _¿Cuál es el formato de las cabeceras?_

       Las cabeceras están formadas por el nombre de la cabecera, seguido de ":", y a continuación el valor de la cabecera, que no puede contener saltos de línea. Los espacios a su izquierda se ignoran.

    3. _Suponga que se desea realizar un requerimiento de HTTP 1.1 usando curl/7.74.0 a un sitio como "www.misitio.com" para obtener el recurso "/index.html". En base a lo indicado, ¿qué información debería enviarse como encabezado? Indique cómo quedaría el requerimiento._

       Si se quisiera realizar ese requisito, la información enviada en cabeceras sería principalmente la de Host, indicando la página deseada. El requisito quedaría de la siguiente manera: 

       ```
       GET /index.html HTTP/1.1
       Host: www.misitio.com
       ```

---

7. _Utilizando la VM, abra una terminal e investigue sobre el comando curl. Analice para qué sirven los siguientes parámetros (-I, -H, -X, -s)._

   Utilizando el comando `man curl`, se puede ver el manual para el comando curl. Si se envía la salida a grep con el parámetro para que muestre más líneas, y cada uno de los parametros se puede buscar cada uno. Las funciones de los parametros son:

    * `man curl | grep -A 6 -- -I`: realiza un requisito HEAD de HTTP.
    * `man curl | grep -A 6 -- -H`: permite enviar headers extra cuando se realiza un requisito HTTP. Se puede enviar cualquier cantidad de headers extra.
    * `man curl | grep -A 6 -- -X`: se usa para especificar el método que se enviará en el requisito HTTP, en lugar del método default de curl que es GET.
    * `man curl | grep -A 6 -- -s`: usa curl en modo silencioso, solo muestra el output de data requerido.

   > Se usa el doble guión (--) debido a que quiero buscar una opción, y si no se usara grep lo interpretaría como intentar usar un parámetro.

---

8. _Ejecute el comando curl sin ningún parámetro adicional y acceda a www.redes.unlp.edu.ar. Luego responda:_

    1. _¿Cuántos requerimientos realizó y qué recibió? Pruebe redirigiendo la salida (>) del comando curl a un archivo con extensión html y abrirlo con un
navegador._

       Cuando se realiza el requisito de la página y se redirige a un archivo HTML, se realiza un único requisito pidiendo el archivo "/", y si luego se abre el archivo desde el navegador, no se realizarán requisitos por parte del navegador, ya que el archivo ya se tiene en la computadora, y se accede usando el protocolo file:// desde el navegador, en lugar del http://.

    2. _¿Cómo funcionan los atributos href de los tags link e img en html?_

       Estos atributos indican qué recurso se requiere para el elemento necesario.

    3. _Para visualizar la página completa con imágenes como en un navegador, ¿alcanza con realizar un único requerimiento?_

       No, ya que los elementos como imágenes, archivos CSS de estilo, archivos de script, o incluso fuentes tipográficas pueden ser requeridas indicando un href. Se debe realizar requisitos de esos recursos también.

    4. _¿Cuántos requerimientos serían necesarios para obtener una página que tiene dos CSS, dos Javascript y tres imágenes? Diferencie cómo funcionaría un navegador respecto al comando curl ejecutado previamente._

       Se requiere de 8 requisitos: la página como tal, y los elementos indicados. La diferencia entre curl y el navegador, es que curl sólo hace el requisito indicado en el comando, mientras que el navegador detecta los elementos que necesitan requisitos, y las realiza para poblar los elementos.

---

9. _Ejecute a continuación los siguientes comandos:_

   _curl -v -s www.redes.unlp.edu.ar > /dev/null_
   _curl -I -v -s www.redes.unlp.edu.ar_

    1. _¿Qué diferencias nota entre cada uno?_

       Ambos dan salidas similares: primero, la request, luego, los headers de la response. En el caso del segundo comando se indica -v, que es verbose, y muestra cada uno de los headers que se van recibiendo en la respuesta, a la vez que se usa -I, que realiza un request HEAD, por lo que los headers se muestran repetidos. En cambio en el primero se hace un GET y se indica verbose, lo cual hace que se vayan mostrando esos headers, pero se envía el resto de la respuesta a /dev/null que lo elimina.

    2. _¿Qué ocurre si en el primer comando se quita la redirección a /dev/null? ¿Por qué no es necesaria en el segundo comando?_

       En el primer comando, si se elimina la redirección, se mostrará el recurso pedido además de las cabeceras, ya que se está realizando el método GET, que en el cuerpo presenta el recurso. Para el segundo comando no se requiere la redirección porque se realiza el método HEAD, que sólo da las cabeceras.

    3. _¿Cuántas cabeceras viajaron en el requerimiento? ¿Y en la respuesta?_

       En el requisito se envían 3 cabeceras, Host, User-Agent y Accept. En la respuesta se presentan 7 cabeceras.

---

10. _¿Qué indica la cabecera Date?_
  
    La cabecera Date indica la fecha y hora en que se realizó la response al requisito.

---

11. _En HTTP/1.0, ¿cómo sabe el cliente que ya recibió todo el objeto solicitado de manera completa? ¿Y en HTTP/1.1?_

    En HTTP/1.0 la sesión se cerraba automáticamente por defecto, permitiendo al cliente saber que se recibió la totalidad de la respuesta. 

    En HTTP/1.1, se cambió la funcionalidad por defecto a keep-alive, que mantiene la sesión abierta por más tiempo a la espera de más requisitos. Por eso, se indica en una de las cabeceras de la respuesta el largo del contenido, permitiendole saber cuando el mensaje se completaba.

---

12. _Investigue los distintos tipos de códigos de retorno de un servidor web y su significado. Considere que los mismos se clasifican en categorías (2XX, 3XX, 4XX, 5XX)._

    Los códigos de retorno se clasifican en:
    * 100: Indican que la operación se está procesando
    * 200: Indican que se realizó la operación con éxito
    * 300: Indican que se debe redireccionar
    * 400: Indican errores de cliente, como requisitos mal hechos o recursos no encontrados
    * 500: Indican errores de servidor ante requisitos aparentemente correctos
