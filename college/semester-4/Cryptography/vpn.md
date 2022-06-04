# Virtual Private Network

<!-- > Es una red cuyas conexiones son establecidas de manera segura entre sus participantes a través de la infraestructura existente en internet, mediante técnicas de cifrado, que brindan autenticidad, confidencialidad e integridad, lo cual impide que alguien ajeno a la comunicación entre dichos participantes pueda espiarla y sepa quienes son sus participantes. -->

> An encrypted connection over the Internet from a device to a network. The encrypted connection helps ensure that sensitive data is safely transmitted. It prevents unauthorized people from eavesdropping on the traffic and allows the user to conduct work remotely.  VPN technology is widely used in corporate environments.

## Types of VPN

- A nivel cliente:
  - cualquier dispositivo terminal puede bajar una aplicación para a través de ella conectarse a a una red o por otra parte puede utilizar las opciones de configuración que da el sistema operativo, en este caso, el usuario se percata de su uso y tiene interacción con la aplicación para configurarla, todo a nivel usuario, no a nivel experto
- A nivel red:
  - las conexiones entre 2 o más redes se llevan a cabo a través de routers mediante reglas de configuración establecidas con ACLs. En este caso el usuario final no se entera de su uso, ni tiene interacción para configurar, ya que de esto por lo general se encargan las personas de it
  
## What it offers

- Ahorro: no es necesario crear nueva infraestructura o tener enlaces dedicados que puedan ser costosos
- Escalabilidad: aprovecha lo que existe en Internet para crear una red de esta naturaleza, evitando agregar complejidad adiocional a su creación, configuración y mantenimiento
- Compatibilidad
- Seguridad
- Funcionalidad

## IP Security (IPSec)

Trabaja desde la capa 3 del modelo OSI

Formado de las siguientes partes:

1. Modo: authentication header, encapsulated security payload, mixto
2. Confidencialidad: algoritmos simétricos tales como 3DES, AES, etc.
3. Integridad: funciones resumen o hash como la familia SHA
4. Autenticación: algoritmos asimétricos o de clave pública tales como RSA o curvas elípticos. Tambien existe la posibilidad de usar claves pre-compartidas denotadas como PSK. Parecido a lo que ocurre con redes inalámbricas
5. Intercambio de secretos: algoritmos asimétricos tales como Diffie-Hellman identificados con números tipo DH14, DH15, DH16, etc., que implica el uso de un tamaño de clave y de una versión, ya sea basada en generadores o en el uso de curvas elípticas

## Extra ?

Modo AH no incluye el aspecto de confidencialidad, solo incluye la autenticación, la integridad y el intercambio de secretos. La trama AH puede verse así

Encabezado IP, AH, Datos

Modo ESP sí incluye el aspecto de confidencialidad junto a todo lo demás:

Nuevo Encabezado IP, Encabezado ESP, Encabezado IP, Datos, ESP Trailer, ESPA
Claro, Claro, Cifrado, Cifrado, Cifrado, Claro
Claro, Claro, Cifrado, Cifrado, Cifrado, Claro

<!-- Para simplificar, Autenticación ESP = ESPA -->

Modos de envío

Modo Transporte: No enmascara el origen y el destino

Modo Tunelado: sí enmascara el origen y el destino

## Protocolo Internet Key Exchange (IKE)

## For the flex

[SHA](https://www.youtube.com/watch?v=DMtFhACPnTY)
