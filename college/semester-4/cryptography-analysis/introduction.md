# Introduction

- [Introduction](#introduction)
  - [Cryptography](#cryptography)
    - [An old definition](#an-old-definition)
    - [Cryptography reborn](#cryptography-reborn)
  - [Basics](#basics)
  - [Crypto-analysis](#crypto-analysis)
  - [Cryptology](#cryptology)
  - [Information](#information)
    - [Types of information](#types-of-information)
  - [Cybersecurity](#cybersecurity)
  - [Metrics](#metrics)
  - [Properties](#properties)
  - [Perfect Secrecy](#perfect-secrecy)
  - [Kerckhoffs' principles](#kerckhoffs-principles)

## Cryptography

### An old definition

> Branch of mathematics, informatics and telematics that makes use of several methods and techniques with the purpose of ciphering, and so, protect a message or file through an algorithm, using one or more keys

### Cryptography reborn

> Branch of mathematics and engineering that studies the application of methods and techniques (both physical and mathematical) that permit the protection and validation of sensitive information through ciphering, authentication, integrity checking and masking through one or several algorithms using one or more keys in combination with extra data

## Basics

- Plain-text: information before encryption (text, files, etc...)
- Cipher-text: information that has been encrypted (text, files, etc...) through a specific algorithm. Unreadable for anyone, it needs to be decrypted to be readable
- Key: sequence of characters and numbers that is used to encrypt or decrypt a message

## Crypto-analysis

- Brute Force: check every possible key until the ciphertext is decrypted
- Ciphertext: the attacker has hold of several ciphertexts, but not the original plain-text
- Known-plaintext: the attacker has access to ciphertexts and knows the plain-text that generated them
- Chosen-plaintext: the attacker chooses common plain-texts and analyzes the generated ciphertexts
- Chosen-ciphertext: the attacker choses common ciphertexts and analyzes the generated plain-texts

## Cryptology

> Branch of mathematics and engineering that studies the application of methods and techniques (both physical and mathematical) that permit the protection and validation of sensitive information through ciphering, authentication, integrity checking and masking through one or several algorithms using one or more keys in combination with extra data; while at the same time it enables the study and exploitation of the vulnerabilities of the cryptographic system with the goal of extracting _sensitive_ data through the keys.

## Information

> Set of readable data (text, files, messages, etc...) that is created through a representation language that must be protected from external threats during its transmission or storage, using cryptographic techniques among other tools

### Types of information

- **Non-sensitive**: its knowledge does not compromise the integrity of a system or the original user
- **Sensitive**: its knowledge compromises the integrity of a system or the original user or a third party.
  - In general, this type of information is just meant for the sender and the receiver

## Cybersecurity

> Branch of engineering that studies the protection of sensitive information in storage, processing and transmission systems through different tools, techniques, methods and processes used as countermeasures against attacks from un-authorized users or possible threats, where different people have roles of either direct access or awareness for their adequate usage

## Metrics

- Security level: amount of work required to break the encryption
- Functionality: level of objectives met for the protection of the information when encryption is performed (e.g. confidentiality, integrity, availability)
- Operation method: refers to the way the crypto-system is designed and implemented
- Performance: relation between the quantity of encrypted information, speed of encryption and the physical resources needed
- Ease of implementation: refers to the complexity of the adaption of the crypto-system to a specific environment (hardware and software)

## Properties

Every good cryptographic system must possess the following properties to be considered resilient to attacks

- **Confusion**: to hide the relationship between the ciphertext and the key
  - At a lower level, it means that each binary digit of the ciphertext should depend on several parts of the key
- **Diffusion**: to hide the statistical relationship between the ciphertext and the plain-text
  - If we change a single bit of the plain-text, then around half of the bits in the ciphertext should change, and viceversa.

## Perfect Secrecy

> A ciphertext maintains perfect secrecy if the attacker’s knowledge of the contents of the message is the same both before and after the adversary inspects the ciphertext, attacking it with unlimited resources. That is, the message gives the adversary precisely no information about the message contents.

## Kerckhoffs' principles

1. The system must be practically, if not mathematically, indecipherable
2. It should not require secrecy, and it should not be a problem if it falls into enemy hands
3. It must be possible to communicate and remember the key without using written notes, and correspondents must be able to change or modify it at will
4. It must be applicable to telegraph communications
5. It must be portable, and should not require several persons to handle or operate
6. Given the circumstances in which it is to be used, the system must be easy to use and should not be stressful to use or require its users to know and comply with a long list of rules

As I'm sure you can guess, most of these rules are outdated, all of them but the second axiom which is still critically important
