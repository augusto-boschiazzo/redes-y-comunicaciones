# Practica 1

### Capa de Aplicación - HTTP

---

1. _¿Cuál es la función de la capa de aplicación?_

   La capa de aplicación está compuesta de servicios de comunicación a los usuarios, User Interfaces, aplicaciones construidas sobre la red, y protocolos de comunicación como HTTP, SMTP, etc. 

   La función de la capa de aplicación varía según el end system: el cliente hace peticiones y presenta las respuestas, el servidor recibe peticiones, las procesa y responde.

   La capa de aplicación se encuentra presente sólo en los end systems, no en links y switches, que sólo tienen la capa de red y sus capas inferiores para poder direccionar los mensajes.

2. _Si dos procesos deben comunicarse:_

    1. _¿Cómo podrían hacerlo si están en distintas máquinas?_

       La forma en la que se pueden comunicar dos procesos de distintas máquinas es a través de una interfaz de software llamada **socket**. 

       Cuando un proceso se quiere comunicar con el proceso de otra máquina, debe conocer su IP, para saber a dónde enviar los mensajes. Pero también debe conocer el **número de puerto**, que indica al socket de qué proceso enviar la información.

    2. _Y si están en la misma, ¿qué alternativas existen?_

       
