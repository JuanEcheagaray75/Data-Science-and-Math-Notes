# Firewall

- [Firewall](#firewall)
  - [Variants](#variants)
    - [Proxy](#proxy)
    - [Stateful Inspection](#stateful-inspection)
    - [Unified Threat Management (UTM)](#unified-threat-management-utm)
    - [Next Generation (NGFW)](#next-generation-ngfw)
    - [Threat Focused NGFW](#threat-focused-ngfw)
    - [Virtual](#virtual)
  - [Review](#review)

> Network security device that monitors incoming and outgoing network traffic, and decides whether to allow or block specific traffic based on a defined set of security rules

## Variants

### Proxy

Serves as the gateway from one network to another for a specific application, can provide additional functionality such as content caching and security by preventing direct connections from outside the network. This may also impact throughput capabilities and the applications they can support.

### Stateful Inspection

Allows or blocks traffic based on state, port and protocol. It monitors all activity from the opening of a connection until it is closed. Filtering decisions are made based on both administrator-defined rules as well as context, which refers to using information from previous connections and packets belonging to the same connection.

### Unified Threat Management (UTM)

> An approach to information security where a single hardware or software installation provides multiple security functions.

Combines the functions of a stateful inspection firewall with intrusion prevention and antivirus. It may also include additional services and often cloud management. UTM's focus on simplicity and ease of use.

### Next Generation (NGFW)

Designed to block modern threats such as advanced malware and application layer attack. A NGFW must include:

1. Standard firewall capabilities like stateful inspection
2. Integrated intrusion prevention
3. Application awareness and control to see and block risky apps
4. Upgrade paths to include future information needs
5. Techniques to address evolving security threats

### Threat Focused NGFW

Includes all the capabilities of a traditional NGFW and also provide advanced threat detection and remediation, with a firewall such as this you can:

1. Know which assets are most at risk with complete context awareness
2. Quickly react to attacks with intelligent security automation that sets policies and hardens your defenses dynamically
3. Better detect evasive or suspicious activity with network and endpoint event correlation
4. Greatly decrease the time from detection to cleanup with retrospective security that continuously monitors for suspicious activity and behavior even after initial inspection
5. Ease administration and reduce complexity with unified policies that protect across the entire attack continuum

### Virtual

Deployed as a virtual appliance in a private cloud (VMware ESXi, Microsoft Hyper-V) or public cloud (AWS, Azure, Google, Oracle) to monitor and secure traffic across physical and virtual networks. A virtual firewall is often a key component in software-defined networks (SDN).

## Review

- Access control lists (ACLS)
- Zona desmilitarizada
