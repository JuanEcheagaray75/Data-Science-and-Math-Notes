# Network Security

## OSI model (Open System Interconnection)

> A conceptual model that describes the universal standard of communication functions of a telecommunication system or computing system, without any regard to the system's underlying internal technology and specific protocol suites

### Layer Architecture

1. Physical layer: Transmission and reception of raw bit streams over a physical medium
   - PDU: Bit, symbol
2. Data Link layer: Transmission of data frames between 2 nodes connected by a physical layer
   - PDU: Frame
   - Ethernet Protocol
3. Network layer: Structuring and managing a multi-node network, including addressing, routing and traffic control
   - PDU: Packet
   - Internet Protocol
4. Transport layer: Reliable transmission of data segments between points on a network, including segmentation, acknowledgement and _multiplexing_
   - PDU: Segment, datagram
   - UDP, TCP protocol
5. Session layer: Managing communication sessions, i.e., continuous exchange of information in the form of multiple back-and-forth transmissions between two nodes
   - PDU: Data
6. Presentation layer: Translation of data between a networking and an application; including character encoding, data compression and encryption-decryption
   - PDU: Data
7. Application layer: High-level APIs, including resource sharing, remote file access
   - PDU: Data
   - DNS, FTP, HTTP, HTTPS, etc...

DHCP => Dynamic Host Control Protocol
IETF => Internet Engineering Task Force2

## TCP (Transfer Control Protocol)

## New commands

```ps1
nslookup website-adress.com
```
