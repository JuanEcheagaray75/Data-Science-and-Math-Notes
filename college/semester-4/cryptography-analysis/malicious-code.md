# Malicious code

- [Malicious code](#malicious-code)
  - [Fundamentals](#fundamentals)
    - [Consequences](#consequences)
    - [Objectives](#objectives)
    - [Actions taken by attackers](#actions-taken-by-attackers)
    - [What can happen](#what-can-happen)
    - [Environments used](#environments-used)
  - [Taxonomy](#taxonomy)
    - [Viruses](#viruses)
    - [Worms](#worms)
    - [Trojans](#trojans)
    - [Cross-site scripting cross-site reference video](#cross-site-scripting-cross-site-reference-video)
    - [Backdoor](#backdoor)
    - [Data files with malicious code](#data-files-with-malicious-code)
    - [Spyware](#spyware)
    - [Exploits](#exploits)
    - [Ransomware](#ransomware)
  - [How they achieve success](#how-they-achieve-success)
    - [Phishing](#phishing)
    - [Pharming](#pharming)
    - [Botnet](#botnet)
  - [Countermeasures](#countermeasures)
  - [Common attacks](#common-attacks)
    - [Denial of Service](#denial-of-service)
    - [DNS Spoofing](#dns-spoofing)
    - [DNS Hijacking](#dns-hijacking)

> Malicious code is harmful computer programming scripts designed to create or exploit system vulnerabilities. This code is designed by a threat actor to cause unwanted changes, damage, or ongoing access to computer systems. Malicious code may result in back doors, security breaches, information and data theft, and other potential damages to files and computing systems.

## Fundamentals

### Consequences

- Data corruption
- Denial of service
- Sensitive information theft
- Blackmailing
- Inconvenience

### Objectives

- To expose a victim to malicious code
- Access sensitive information
- Monitor the vulnerable system
- To damage the system in a critical way

### Actions taken by attackers

- To test and research a vulnerability
- Develop programs to exploit a vulnerability
- Expose the system to malicious code
- Execute malicious code on its own or through a third party software

### What can happen

- Modification of the data within the system
- Corruption or deletion of data
- Obtain sensitive information
- To gain access to restricted resources
- Execution of dissemination and control activities.

### Environments used

- Devices with direct access to the system, like USB drives
- Wireless Networks, wifi mainly
- Exchange information systems, like email
- Online networks

## Taxonomy

### Viruses

Viruses are self-replicating code that attaches to macro-enabled programs to execute. These files travel via documents and other file downloads, allowing the virus to infiltrate your device. Once the virus executes, it can self-propagate and spread through the system and connected networks.

### Worms

They are also self-replicating and self-spreading code like viruses, but do not require any further action to do so. Once a computer worm has arrived on your device, these malicious threats can execute entirely on their own, without any assistance from a user-run program.

### Trojans

Trojans are decoy files that carry malicious code payloads, requiring the user to use the file or program to execute. These threats cannot self-replicate or spread autonomously. However, their malicious payload could contain viruses, worms, or any other code.

### Cross-site scripting [cross-site reference video](https://www.youtube.com/watch?v=L5l9lSnNMxg)

Cross-site scripting interferes with the user's web browsing by injecting malicious commands into the web applications they may use. This often changes web content, intercepts confidential information, or serves an infection to the user's device itself.

### Backdoor

Application back door access can be coded to give a cybercriminal remote access to the compromised system. Aside from exposing sensitive data, such as private company information, a backdoor can allow an attacker to become an advanced persistent threat (APT).

Cybercriminals can then move laterally through their newly obtained access level, wipe out a computer's data or even install spyware, these threats can reach a high level.

### Data files with malicious code

Non-executable files that take advantage of the weaknesses in the software used to open them. They are widely used to install malicious software commonly distributed on the internet, common examples are zip files, files used by Adobe or Office, even PDFs!

### Spyware

It's loosely defined as malicious software designed to enter your computer device, gather data about you and forward it to a third-party without your consent. Spyware can also refer to legitimate software that monitors your data for commercial purposes, like advertising. However, malicious spyware is explicitly used to profit from stolen data.

### Exploits

Exploits are a subset of malware. These malicious programs contain data or executable code, which is able to take advantage of one or more vulnerabilities in the software running on a local or remote computer.

Put simply: You have a browser and there is a vulnerability in it that allows "an arbitrary code" to run (i.e. install and launch some malicious program) on your system without your knowledge. Most often the first step for the attackers is allowing privilege escalation, so they can do anything with the attacked system.

### Ransomware

Ransomware is extorsion software that can lock your computer and then demand a ransom for its release. In most cases, ransomware infection occurs as follows. The malware first gains access to the device, depending on the type of ransomware, either the entire operating system or individual files are encrypted, a ransom is then demanded from the victim.

## How they achieve success

To guarantee its success, cybercriminals combine malicious software with _social engineering_, that broadly, is a technique that allows attackers to gather information through the manipulation/deception of the potential victims to get their sensitive data.

### Phishing

Type of internet fraud that seeks to acquire a user's credentials through deception. It includes theft of passwords, credit card numbers, bank account details and other confidential information.

Phishing messages usually take the form of fake notifications from banks, providers, e-pay systems and other organizations. The notification will try to encourage the recipient, for one reason or another to urgently enter/update their personal data. Such excuses often relate to loss of data, system breakdown, etc...

### Pharming

A type of cyberattack intended to covertly redirect users to a phishing resource owned by the attacker. Pharming works by substituting the IP address of a legitimate site by means of malware installed on the victim's computer.

Redirection is achieved by modifying the `hosts` file or DNS server settings. The list of domains whose IP addresses are to be spoofed is determined by the attacker.

### Botnet

Botnets are networks of hijacked computer devices used to carry out various scams and cyberattacks. The term botnet is formed from the word robot and network. Assembly of a botnet is usually the infiltration stage of a multi-layer scheme. The bots serve as a tool to automate mass attacks, such as data theft, server crashing and malware distribution.

## Countermeasures

- Antivirus software: an up-to-date database is the ideal solution to counter malware. Nevertheless, nowadays the industry is leaning towards machine learning based solutions to detect malware on a device
- Verify carefully any link or attached file we receive
- Allow or web-browser to block pop-ups from un-trusted websites
- Use accounts with limited privileges, do not allow users to change sensitive settings or access sensitive data without their permission
- Deactivate services such as auto-play or auto-run, ideally every app must ask permission to be installed
- Change passwords: change your password to a strong one, it should include alphabetical characters, numbers and special characters
- Keep software updated: regularly check for updates to your software
- Use firewalls: block all incoming connections to your computer
- Use anti-spyware: many antiviruses already have some anti-spyware features
- Monitor accounts: take control of what each user does on their account
- Avoid using public Wi-Fi: do not fall into temptation, if you can, use a VPN
- Honey-nets: designed to catch an intruder into an isolated environment and understand his/her behavior

## Common attacks

### Denial of Service

A DoS attack is designed to hinder or stop the normal functioning of a website, server or other network resource. There are various ways for attackers to achieve this, but in general terms it involves manipulating the way incoming data is handled by the server to overload it with network traffic. This prevents it from carrying out its normal functions and in some circumstances crashes the server completely.

### DNS Spoofing

A computer hacking attack, whereby data is introduced into a Domain Name System resolver's cache, causing the server to return an incorrect IP address, diverting traffic to the attacker's computer (or any other computer).

### DNS Hijacking

An attack that involves the interception of DNS queries. Cybercriminals use malware to change the IP address of a resource linked to a specific domain name, and redirect victims to their own website instead of the one initially requested. Sone ISPs use DNS hijacking to display ads and collect statistics.
