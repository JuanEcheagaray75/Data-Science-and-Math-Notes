# Block Ciphers

- [Block Ciphers](#block-ciphers)
  - [Feistel Networks (DES)](#feistel-networks-des)
    - [Symmetric Key](#symmetric-key)
  - [Simple Permutation Networks (AES)](#simple-permutation-networks-aes)

## Feistel Networks (DES)

### Symmetric Key

- Cifrado en bloques de tamaño de 64 bits
  - 8 bytes de memoria encriptados en un bloque
- Se usa una clave de tamaño de 56 bits
  - Hay un total de $2^{56} > 7 \times 10^{16}$ claves posibles
- La clave es simétrica
- Usa 16 rondas de encriptado con la misma estructura interna
- Hay una sub-clave distinta para cada ronda
- LA estructura de DES es llamada Feistel Network
- Se realiza una permutación de bits al inicio y al final

## Simple Permutation Networks (AES)
