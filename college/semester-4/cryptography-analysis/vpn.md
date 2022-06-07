# Virtual Private Network

> An encrypted connection over the Internet from a device to a network. The encrypted connection helps ensure that sensitive data is safely transmitted. It prevents unauthorized people from eavesdropping on the traffic and allows the user to conduct work remotely.  VPN technology is widely used in corporate environments.

## Types of VPN

### Remote access

A remote VPN securely connects a device outside the corporate office. These devices are known as endpoints and may be laptops, tablets or smartphones. Any endpoint device can download an app that will permit it to connect to the corporate network, it's important to note that the user will not have all the privileges of a super user to configure it to their liking.

### Site to site

Connects the corporate offices to branch offices over the internet. Site-to-site VPNs are used when distance makes it impractical to have direct network connections between these offices. Dedicated equipment is used to establish and maintain a connection. Think of site to site VPNs as network to network.

These connections between 2 or more networks take place between routers configured with established ACLs. For this implementation, the end user doesn't even notice, nor has he any interaction on the configuring process, only IT staff.
  
## What it offers

- All traffic is confidential, and its integrity and authenticity is guaranteed through the use of cryptography.
- Allows user to anonymize their IP address. (A better term will be mask)
- Savings: no need to create a new infrastructure or have dedicated servers that might be costly.
- Scalability: takes advantage of the existing network infrastructure, does not add that much complexity to its creation, configuration and maintenance, plus, it can easily be connected and disconnected
- Compatibility: it uses protocols/software that is widely used by every modern device.
- Security: confidentiality, authenticity and integrity, and a little bit of anonymity.
- Functionality: contrary to a proxy server configured on a web browser or what happens with HTTPS over SSL, all the generated traffic goes through the VPN

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
