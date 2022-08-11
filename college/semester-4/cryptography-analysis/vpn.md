# Virtual Private Network

- [Virtual Private Network](#virtual-private-network)
  - [Types of VPN](#types-of-vpn)
    - [Remote access](#remote-access)
    - [Site to site](#site-to-site)
  - [What it offers](#what-it-offers)
  - [Common uses](#common-uses)
  - [Architecture of a Site-to-Site VPN](#architecture-of-a-site-to-site-vpn)
  - [IP Security (IPSec)](#ip-security-ipsec)
    - [IPSec framework](#ipsec-framework)
    - [Differences between the protocols](#differences-between-the-protocols)
    - [Delivery modes](#delivery-modes)
      - [Transport mode](#transport-mode)
      - [Tunneling mode](#tunneling-mode)
  - [Internet Key Exchange (IKE)](#internet-key-exchange-ike)
  - [For the flex](#for-the-flex)

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

## Common uses

- Remote working
- Avoid censorship and content blocking

> Beware of the used VPN, the service providers have full access to our traffic.

## Architecture of a Site-to-Site VPN

- Network with endpoint devices
- Routers to configure for usage of the VPN
- Communication channel between the routers

One of the ways to set up a Site-to-Site VPN is through the use of the IPSec protocol.

## IP Security (IPSec)

> A secure network protocol suite that authenticates and encrypts the packets of data to provide secure encrypted communication between 2 computers over an Internet Protocol Network

IPSec works on the layer 3 of the OSI model, it must be done this way to provide the anonymity desired by the end users

### IPSec framework

1. Mode/Protocol: Authentication Header (AH), Encapsulated Security Payload (ESP), mixed
2. Confidentiality: achieved through symmetric encryption algorithms such as 3DES, AES; all of their versions can be used
3. Integrity: achieved through hash algorithms such as MD5, or the SHA family, the latter being the best choice
4. Authentication: achieved with asymmetric algorithms such as RSA, elliptic curves. It can also be done with Pre-Shared Keys (PSK), similar to the ones used to connect to wifi networks
5. Secret exchange: performed with asymmetric algorithms like Diffie-Hellmann. They are identified by numbers such as DH14, DH15, DH19, DH20. They define a certain key size and version, said key may be forged through generators or elliptic curves.

### Differences between the protocols

The Authentication Header mode does not include the aspect of confidentiality, it only covers authentication, integrity and secret exchange, a packet sent with AH looks something like this:

| IP Header |  AH   | Data  |
| :-------: | :---: | :---: |

The IP header is authenticated with a key.

The ESP mode does indeed include confidentiality:

| New IP Header | ESP Header | IP Header |   Data   | ESP Trailer | ESPA  |
| :-----------: | :--------: | :-------: | :------: | :---------: | :---: |
|     Plain     |   Plain    | Ciphered  | Ciphered |  Ciphered   | Plain |

### Delivery modes

#### Transport mode

> Does not mask the source and destination

Only the payload of the IP packet is usually encrypted or authenticated. The routing is intact, since the IP header is neither modified nor encrypted; however when the authentication header is used, the IP addresses cannot be modified by NATs (Network Address Translation), as this always invalidates the hash value. The transport and application layers are always secured by a hash, so they cannot be modified in any way.

#### Tunneling mode

> Does mask the source and destination

The entire IP packet is encrypted and authenticated. It is then encapsulated into a new IP packet with a new IP header. Tunnel mode is used to create VPNs for network to network communications, host to network communications and host to host communications. Tunnel mode does support NAT traversal.

## Internet Key Exchange (IKE)

It allows us to establish the same parameters between the origin and destination endpoints. As an example, say the source needs:

1. IPSec protocol: Mixed (AH, ESP)
2. Confidentiality: AES-128
3. Integrity: SHA-1
4. Authentication: PSK
5. Secret exchange: DH14

Then the destination endpoint must use the same settings in order for a connection to be established. IKE uses UDP as the transport protocol in the OSI model, it is communicated through port 500.

## For the flex

[SHA](https://www.youtube.com/watch?v=DMtFhACPnTY)
