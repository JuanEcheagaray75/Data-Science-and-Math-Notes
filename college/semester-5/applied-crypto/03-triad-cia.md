# CIA Triad model

- [CIA Triad model](#cia-triad-model)
  - [Confidentiality](#confidentiality)
  - [Integrity](#integrity)
  - [Availability](#availability)
  - [Concepts](#concepts)

[Main reference](https://www.fortinet.com/resources/cyberglossary/cia-triad)

## Confidentiality

> Data is kept secret or private

Confidentiality involves the effort of an organization to make sure data is kept secret or private. To achieve this, access to information must be controlled to prevent unauthorized sharing of data-whether intentional or accidental. A key component of maintaining confidentiality is making sure that people without proper authorization are prevented from accessing assets important to your business. Conversely, an effective system also ensures that those who have access have the necessary privileges.

For example, those who work with an organization's finances should be able to access the spreadsheets, bank accounts, and other information related to the flow of the money. However the vast majority of the other employees (and perhaps even certain executives- may not be granted access). To ensure these policies are followed, stringent restrictions have to be in place to limit who can see what.

To fight against confidentiality breaches, you can easily classify and label restricted data, enable access control policies, encrypt data and use Multi-Factor Authentication (MFA) systems.

## Integrity

> Data is trustworthy and free from tampering

The integrity of your data is maintained only if the data is authentic, accurate, and reliable. For example, if your company provides information about senior managers on your website, this information needs to have integrity. If it's inaccurate, those visiting the website or information may feel your organization is not trustworthy. Someone with a vested interest in damaging the reputation of your organization may try to hack your website and alter the descriptions, photographs, etc...

To protect the integrity of your data, you can use hashing, encryption, digital certificates or digital signatures. For websites you can employ trustworthy certificate authorities that verify the authenticity of your website, so your customers know they are visiting the site they intended to visit.

A method for verifying integrity is non-repudiation, which refers to when something cannot be repudiated or denied.

## Availability

> Data must also be available to those who need it

Even if data is kept confidential and its integrity maintained, it is often useless unless it is available to those in the organization and the customers they serve. This means that systems, networks, and applications must be functioning as they should and when they should. Also, individuals with access to specific information must be able to consume it when they need to, and getting to the data should not take an inordinate amount of time.

To ensure availability, organizations can use redundant networks, servers and applications. These can be programmed to become available when the primary system has been disrupted or broken. You can also enhance availability by staying on top of upgrades to software packages and security systems. In this way, you make it less likely for an application to malfunction.

## Concepts

1. **Telemetry**: in situ collection of measurements or other data at remote points and their automatic transmission to receiving equipment for monitoring.
   1. In software, telemetry is used to gather data on the use and performance of applications and application components. In some cases, very detailed data is reported like individual window metrics, count of used features, and individual function timings.
2. **Victimology**: studying victims of crimes, the emotional and psychological effects of the crime, and relationships between perpetrators and victims.
3. **Emotet**:
   1. Originally designed as a banking malware that attempted to sneak onto your computer and steal sensitive and private information. Later versions of the software saw the addition of spamming and malware delivery services
   2. Uses functionality that helps the software evade detection by some anti-malware products; uses worm-like capabilities to help to other connected computers
   3. Primarily spread through spam emails, the infection may arrive either via malicious scripts, macro-enabled document files or malicious links. Emotet emails may contain familiar branding designed to look like a legitimate email (_Your invoice, Payment details, etc..._).
   4. It uses a number of tricks to try and prevent detection and analysis, notably, Emotet knows if it's running inside a VM, it will lay dormant if it detects it's inside one
   5. Also uses Command and Control servers to receive updates, allowing attackers to install malware updates, install additional malware or act as a dumping ground for stolen information such as financial credentials.
