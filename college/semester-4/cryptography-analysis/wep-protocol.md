# Wired Equivalence Privacy Protocol (WEP)

- [Wired Equivalence Privacy Protocol (WEP)](#wired-equivalence-privacy-protocol-wep)

> 40 bits key, follows the Challenge and Response scheme, it trusts the user to have the secret key to authenticate itself

- PSK -> Pre-Shared Key

Basa su funcionamiento en el algoritmo RC4, algoritmo de clave privada con arquitectura de cifrado en público, el cual teóricamente opera con claves de 64 bits, pero que en la práctica su clave inicial es de 40 bits, y donde los restantes 24 bits son usados como IV (initialization vector), las sub-claves si son de 64 bits.
