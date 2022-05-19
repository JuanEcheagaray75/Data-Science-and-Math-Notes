# Introduction

## Cryptography

### An old definition

> Branch of mathematics, informatics and telematics that makes use of several methods and techniques with the purpose of ciphering, and so, protect a message or file through an algorithm, using one or more keys

### Cryptography reborn

> Branch of mathematics and engineering that studies the application of methods and techniques (both physical and mathematical) that permit the protection and validation of sensitive information through ciphering, authentication, integrity checking and masking through one or several algorithms using one or more keys in combination with extra data

## Basics

- Plain-text: information before encryption (text, files, etc...)
- Cipher-text: information that has been encrypted (text, files, etc...) through a specific algorithm. Unreadable for anyone, it needs to be decrypted to be readable
- Key: secuencia de caracteres o números que permiten cifrar un texto en claro y descifrar un criptograma

## Crypto-analysis

- Brute Force: a putazo limpio, prueba de todas las claves posibles
- Ciphertext: el atacante conoce varios textos cifrados, pero no los textos en claro que los generaron
- Known-plaintext: texto en claro conocido, el atacante conoce varios criptogramas y tiene conocimientos de qué textos en claro los generaron
- Chosen-plaintext: texto en claro escogido, el atacante elige los textos en claro a probar y revisa cuales criptogramas son obtenidos
- Chosen-ciphertext: texto cifrado escogido. El atacante elige los criptogramas y revisa cuales son los textos en claro obtenidos

## Types of information

- Non-sensitive: su conocimiento no es relevante para comprometer la seguridad de un sistema o el poseedor de la misma.
- Sensitive: su conocimiento puede comprometer la seguridad de un sistema, extensivo a quien es poseedor de dicha información, ocasionando un potencial perjuicio a dicho poseedor o a un tercero.

## Metrics?

- Nivel de seguridad: cantidad de trabajo invertido para romper un algoritmo criptográfico
- Funcionalidad: se refiere al nivel de objetivos cubiertos para fortalecer la detección de información cuando se implementa un algoritmo criptográfico
- Modo de operación: referente a la forma en la cual un criptosistema es implementado
- Desempeño: referente a la cantidad de información que procesa, comparado con la cantidad de recursos físicos utilizados y la velocidad de procesamiento
- Facilidad de implementación: referente a la complejidad de que un criptosistema pueda ser adaptado a entornos de hardware o software

## Properties

- Confusión: relación entre la clave utilizada y el mensaje cifrado sea lo más compleja posible. Esto se logra mediante una operación de sustitución
- Difusión: se busca reacomodar el contenido del mensaje en claro para eliminar cualquier tipo de relación existente entre el mensaje en claro y el criptograma. Esto se logra mediante una operación de transposición o permuta

## Perfect Secrecy

- Needs further reading
- Pretty much useless in practice

## Kerckoff's principles

- EL sistema debería de ser invulnerable en la práctica
- Si los detalles de construcción del sistema son conocidos por un adversario, no debería representar un problema o inconveniente para quienes lo usan
- La clave debería ser fácilmente memorizable y con opción a ser cambiada con esa misma facilidad (outdated)
- El criptograma debería poder transmitirse (_telegráficamente_) electrónicamente
- El dispositivo que encripta debería de ser portable y operable por una sola persona
- El sistema debería de ser fácil de usar, es decir que no se requiera el conocimiento de una larga lista de reglas por parte de quien lo use 

### Extra (just for the flex)

¿Cómo explicar la separabilidad de un perceptrón haciendo uso de álgebra lineal?