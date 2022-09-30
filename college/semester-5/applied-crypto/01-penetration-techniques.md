# Penetration techniques and vulnerability scanning

- [Penetration techniques and vulnerability scanning](#penetration-techniques-and-vulnerability-scanning)
  - [Pre-engagement interactions](#pre-engagement-interactions)
    - [Introduction to Scope](#introduction-to-scope)
    - [Metrics of Time Estimation](#metrics-of-time-estimation)
    - [Scoping Meeting](#scoping-meeting)
    - [Additional Support Based on Hourly Rate](#additional-support-based-on-hourly-rate)
    - [Questionnaires](#questionnaires)
      - [General questions](#general-questions)
    - [Scope Creep](#scope-creep)
    - [Specify start and end dates](#specify-start-and-end-dates)
    - [Dealing with 3rd parties](#dealing-with-3rd-parties)
    - [Define acceptable social engineering pretexts](#define-acceptable-social-engineering-pretexts)
    - [DoS testing](#dos-testing)
    - [Payment terms](#payment-terms)
    - [Goals](#goals)
    - [Establish lines of communication](#establish-lines-of-communication)
    - [Rules of engagement](#rules-of-engagement)
    - [Capabilities and technologies in place](#capabilities-and-technologies-in-place)
  - [Intelligence gathering](#intelligence-gathering)
    - [Intelligence Gathering Levels](#intelligence-gathering-levels)
      - [Compliance driven](#compliance-driven)
      - [Best practices](#best-practices)
      - [State Sponsored](#state-sponsored)
    - [Open Source Intelligence](#open-source-intelligence)
      - [Forms of OSINT](#forms-of-osint)
      - [Data related to the target](#data-related-to-the-target)
  - [Threat modelling](#threat-modelling)
    - [Business Asset Analysis](#business-asset-analysis)
      - [Organizational Data](#organizational-data)
      - [Human Assets](#human-assets)
    - [Business Process Analysis](#business-process-analysis)
    - [Threat Agents/Communities Analysis](#threat-agentscommunities-analysis)
    - [Threat Capability Analysis](#threat-capability-analysis)
    - [Motivation Modelling](#motivation-modelling)
  - [Vulnerability analysis](#vulnerability-analysis)
    - [Testing](#testing)
    - [Active Analysis](#active-analysis)
    - [Passive Analysis](#passive-analysis)
    - [Validation](#validation)
    - [Research](#research)
  - [Exploitation](#exploitation)
  - [Post exploitation](#post-exploitation)
  - [Reporting](#reporting)

The Penetration Testing Execution Standard consists of 7 main sections, these cover everything related to a penetration test - from the initial communication and reasoning behind a pentest, through the intelligence gathering and threat modelling phases where testers are working behind the scenes in order to get a better understanding of the tested organization, through vulnerability research, exploitation and post exploitation, where the technical security expertise of the testers come to play and combine with the business understanding of the engagement, and finally to the reporting, which captures the entire process, in a manner that makes sense to the customer and provides the most value to it.

[Main Reference](http://www.pentest-standard.org/index.php/Main_Page)

## Pre-engagement interactions

> To present and explain the tools and techniques available which aid in a successful pre-engagement step of the penetration test.

### Introduction to Scope

Defining the scope is arguably one of the most important components of a penetration test, yet it is also one of th most overlooked. Neglecting to properly complete pre-engagement activities has the potential to open the penetration tester (or firm) to a number of headaches including scope creep, unsatisfied customers and even legal troubles.

> The scope of a project defines what is to be tested. How each aspect of the test will be conducted will be covered in the Rules of Engagement section

- One key component of scoping an engagement is outlining how the testers should spend their time
- Despite having a solid pricing structure, **the process is not black and white**. It is not uncommon for a customer to be completely unaware of what exactly is what needs to be tested, it's also possible that the client doesn't know how to communicate its needs, sometimes the tester needs to serve as a guide.

### Metrics of Time Estimation

Time estimation are directly tied to the experience of a tester in a certain area. If a tester has significant experience in a certain test he will likely innately be able to determine how long a test will take. If the tester has less experience in the area, re-reading emails and scan logs from previous similar tests the firm has done is a great way to estimate the time requirement for the current engagement. Once the time to test is determined, it is a prudent practice to add 20% to the time.

The extra 20% on the back-end of the time value is called **padding**. Outside of consultant circles, this is also referred to as consultant overhead. Another component of the metrics of time and testing is that every project needs to have a definitive drop dead rate, all well defined projects have a beginning and an end.

### Scoping Meeting

> The goal of the scoping meeting is to define what is to be tested, rules of engagement and costs are not covered during this meeting

1. Establish a Rough Order of Magnitude (ROM) for the project, and validate the assumptions with the client
2. State the range of IPs that will be tested, the client can't just assume that the tester must identify their network and attack it, possible legal issues must be considered
   1. It is the responsibility of the tester to convey the last thought to the client, impart the importance of implicit scoping
   2. Verify that the customer owns all the assets to be tested, for example the DNS servers, email server, the actual hardware their web servers run on and their firewall/IDS/IPS solutions. **If they do not own them, permission from the 3rd party must be obtained**
   3. Consider regional laws, for example, one can't just apply certain techniques of social engineering in certain places of the world, ie. the European Union

### Additional Support Based on Hourly Rate

> Anything that is not explicitly stated within the scope of engagement must be handled very carefully

As the scope of a project increases, resources are consumed and the profits of the tester are reduced, they may even create confusion and anger from the customer side. Any requests outside the original scope should be documented in the form of a **Statement of Work** that clearly identifies and defines the work to be done.

It's recommended that it be clearly stated in the contract that additional work will be done for a flat fee per hour and explicitly state that additional work cannot be performed without a **SoW**.

### Questionnaires

> During initial communications with the customer there are several questions which the client will have to answer in order for the engagement scope to be properly estimated. Below lies a few sample questions which may be asked during this phase:

#### General questions

1. Network Pentest
   1. Why is the customer having the penetration test performed on their environment?
   2. Is the pentest required for a compliance reason?
   3. When does the client want the pentest to be performed?
      1. During business hours?
      2. After business hours?
   4. How many total IP addresses are being tested?
      1. Internal IPs?
      2. External IPs?
   5. Are there any devices that may impact the pentest (firewall, intrusion detection/prevention system, web-app firewall, etc...)?
   6. If the system is penetrated, how is the pentest team to proceed?
      1. Perform a local vulnerability assesment on the machine?
      2. Attempt to get the highest privileges?
      3. Perform no, minimal, dictionary, or brute-force password attacks against the local password hashes obtained?
2. Web Application Pentest
   1. How many web-apps are being tested?
   2. How many log-in systems are being assessed?
   3. How many static/dynamic pages are being tested?
   4. Will the source code be provided?
   5. Will there be any form of documentation?
   6. Will static analysis be performed?
   7. Does the client want **fuzzing** performed on the web-app?
   8. Does the client want role-based testing performed?
   9. Does the client want credential scan performed?
3. Wireless Network Pentest
   1. How many wireless networks are in place?
   2. Is a guest wireless network used?
      1. Does the guest network require authentication?
      2. What type of encryption is used on the wireless network?
      3. What is the square footage coverage?
      4. Will enumeration of rogue devices be performed?
      5. Will the team perform wireless attacks against clients?
      6. Approximately how many clients are connected to the wireless network?
4. Physical Pentest
   1. How many locations are being tested?
   2. Is the physical location a shared facility?
      1. How many floors are being considered? Which of those floors are being tested?
      2. Are there any security guards that will need to be bypassed?
         1. Are they self employed or 3rd party?
         2. Are they armed?
         3. Are they allowed to use force?
      3. How many entrances are there?
      4. Is the use of lock picks or bump keys allowed?
      5. Is the purpose of this test to verify compliance?
      6. What is the square footage of the area in scope
      7. Are all physical security measures documented?
      8. Are video cameras being used?
         1. Are the cameras client owned?
      9. Is there an armed alarm system being used?
         1. Is the alarm silent?
         2. Is the alarm triggered by motion?
         3. Is the alarm triggered by the opening of windows and doors?
5. Social engineering
   1. Does the client have a list of email addresses they would like SE to be performed against?
   2. Does the client have a list of phone numbers they would like SE to be performed against?
   3. Is SE for the purpose of gaining physical access to the clients facilities?
      1. How many people will be targeted?
6. For Business Unit Managers
   1. Is the manager aware of the pentest?
   2. What is the main datum that would create the greatest risk for the client?
   3. Are testing and validation procedures to verify the client's business apps are functioning properly?
   4. Will the testers have access to the Quality Assurance testing procedures from when the apps were developed?
   5. Are Disaster Recovery procedures in place?
7. For System Administrators
   1. Are there any systems that can be tagged as fragile?
   2. Are there systems on the network that the client does not own?
   3. Are Change Management procedures in place?
   4. What is the mean time to repair system outages?
   5. Is any monitoring software in place?
   6. What are the most critical servers and applications?
   7. Are backups tested on a regular basis?
   8. When was the last time the backups were restored?

### Scope Creep

> Refers to changes, continuous or uncontrolled growth in a project's scope, at any point after the project begins.

1. If a customer is pleased with the work done in a particular engagement, it's quite common for them to ask for additional work to be made, do not hesitate to ask for further funding for the extra time spent on the project, if they refuse, it's simply not worth it to stay on to do that work
2. When dealing with existing customers, take care to keep the prices lower. Taking advantage of a good situation by price gouging is an excellent way to lose a client. **The best source for future work is through existing customers**

### Specify start and end dates

### Dealing with 3rd parties

### Define acceptable social engineering pretexts

### DoS testing

### Payment terms

### Goals

### Establish lines of communication

### Rules of engagement

### Capabilities and technologies in place

## Intelligence gathering

- Information gathering on the given organization, the goal is finding attack mediums on the target

### Intelligence Gathering Levels

Defining levels allows us to clarify the expected output and activities within certain real-world constraints such as time, effort, access to information, etc...

#### Compliance driven

Mainly a click-button information gathering process. This level of information can be obtained almost entirely by automated tools (bots)

#### Best practices

#### State Sponsored

### Open Source Intelligence

Search, collection and selection of information coming from public sources for their later use in intel operations. It allows the researcher to collect intel on the possible state of the organization in order to determine a way to breach it, however it doesn't guarantee that the collected intel will still be valid, it might be altered, obsolete, or incomplete.

#### Forms of OSINT

- **Passive Information Gathering**: only useful if there is a very clear requirement that the information gathering activities never be detected by the target
- **Semi-passive Information Gathering**: the goal is to profile the target with methods that would appear like normal traffic internet and behavior, we query only the published name servers for information, we aren't performing in-depth reverse lookups or brute-force DNS requests.
- **Active Information Gathering:**: it should be detected by the target and suspicious or malicious behavior, during this stage we are actively mapping network infrastructure (full port scans with `nmap`), actively enumerating and/or vulnerability scanning the open services.

#### Data related to the target

- **Physical (L1)**: locations and presence, infrastructure, real-state, existing relations
- **Logical (L1/2/3)**: accumulated information for partners, clients and competitors, for each one, a full listing of the business name, business address, type of relationship, basic financial information, basic hosts/network information
- **OrgChart (L1)**: position identification, transactions, affiliates
- **Electronic (L1/2)**: document metadata, marketing communications
- **Infrastructure (L1/2)**: network blocks owned, email addresses, external infrastructure profile, technologies used, purchase agreements
- **Financial (L1)**: reporting, market analysis, trade capital, value history, _EDGAR_ Electronic Data Gathering, Analysis and Retrieval System
- **Individuals**:
  - Employee: History, Social Network Profile, Internet Presence, Physical Location, Mobile Footprint, "For Pay" Information.
- **Covert Gathering**:
  - On-Location Gathering: selecting specific locations for onsite gathering, and then performing reconnaissance over time, one may usually perform physical security inspections, wireless scanning, dumpster diving, types of equipment in use.
  - Offsite Gathering: identifying offsite locations and their importance/relation to the organization, they may include data center locations, network provisioning/provider
- **Human Intelligence**:
- **Footprinting**: 

## Threat modelling

Defines a threat modeling approach as required for a correct execution of a penetration testing. The standard does not impose a specific, but instead requires that the model used be consistent in terms of its representation of threats, their capabilities, their qualifications as per the organization being tested, and the ability to repeatedly be applied to future tests with the same results.

- The standard focuses on **2 key elements** of traditional threat modeling, **assets** and **attacker**. Each one is respectively broken into _business assets_ and _business processes_, and the threat communities and their capabilities.
- Here's a higher level view of the threat modelling process:

1. Gather relevant documentation
2. Identify and categorize primary and secondary assets
3. Identify and categorize threats and threat communities
4. Map threat communities against primary and secondary assets

### Business Asset Analysis

> An asset-centric view is taken on all assets and the business process they support. By analyzing the gathered documentation and interviewing relevant personnel within the organization, the pentester is able to identify the assets that are most likely to be targeted by an attacker.

#### Organizational Data

1. **Policies, plans and procedures**: internal policies, plans and procedures define how the organization does business
2. **Product information**: patents, trade secrets, future plans, source code, supporting systems that directly affect the product market value
3. **Marketing information**: plans for promotions, launches, product changes, positioning, partnerships, 3rd party providers, business plans
4. **Financial information**: bank account information, credit card information and/or credit card numbers, investment accounts, etc...
5. **Technical information**:
   1. _Infrastructure Design_: related to all the core technologies and facilities used to run the organization; building blueprints, technical wiring and connectivity diagrams
   2. _System Configuration_: configuration baseline documentation, configuration checklists and hardening procedures, group policy information, operating system images
   3. _User Account Credentials_: they help facilitate access to the information system, at a non-privileged level as long as there is a means for authentication
   4. _Privileged User Account Credentials_: they help facilitate access to the information system at an elevated level of access. Obtaining privileged user credentials often leads to compromise of the information system being tested
6. **Employee data**: analyzed as any data that can have a **direct** impact on the organization
   1. National Identification Numbers
   2. Personally Identifiable Information
   3. Protected Health Information
   4. Financial Information
7. **Customer data**:
   1. National Identification Numbers
   2. Personally Identifiable Information
   3. Protected Health Information
   4. Financial Information
   5. Supplier Data

#### Human Assets

> Those that could be leveraged to divulge information, manipulated to make decisions or actions that would adversely affect the organization or enable an attacker to further compromise it

1. Executive management
2. Executive assistants
3. Middle management
4. Administrative assistants
5. Technical/Team leads
6. Engineers
7. Technicians
8. Human Resources

### Business Process Analysis

> A business makes money through processes that enhance value of raw goods, this generates revenue. It is crucial to understand the critical vs non-critical process to eventually find flaws and gain further insights on how a threat may act upon the business.

1. **Technical infrastructure supporting process**: business processes are supported by IT infrastructure, all those elements must be identified and mapped
2. **Information assets supporting process**: existing knowledge bases in the organization that are either used as a reference or as support material
3. **Human assets supporting process**: identification of the HR that are involved in the business process should be made in conjuction with the process analysis itself, and every person that has any kind of involvement
4. **3rd party integration and/or usage of/by process**: similar to human assets supporting the process, any 3rd party that has any involvement with the business process should be mapped as well

### Threat Agents/Communities Analysis

|                 Internal                 |               External                |
| :--------------------------------------: | :-----------------------------------: |
|                Employees                 |           Business partners           |
|      Management (executive/middle)       |              Competitors              |
| Administrators (network, system, server) |              Contractors              |
|                Developers                |               Suppliers               |
|                Engineers                 |             Nation States             |
|               Technicians                |            Organized Crime            |
| Contractors (with their external users)  |              Hacktivists              |
|          General user community          | Script Kiddies (recreational hacking) |
|              Remote Support              |                                       |

### Threat Capability Analysis

### Motivation Modelling

> Motivation should be noted for further analysis, their motivations may constantly be changing.

1. Profit
2. Hacktivism
3. Direct grudge
4. Fun / reputation
5. Further access to partner/connected systems
6. Espionage

## Vulnerability analysis

### Testing

> The process of discovering flaws in systems and applications which can be leveraged by an attacker. These flaws can range anywhere from host and service misconfiguration, or insecure application design

### Active Analysis

1. **Automated**: utilizes software to interact with a target, examine responses, and determine whether a vulnerability exists based on those responses. An automated process can help reduce time and labor requirements.
2. **Network/General Vulnerability Scanners**
   1. **Port Based**: one of the first steps taken in traditional pentesting because it helps to obtain a basic overview of what may be available on the target network or host
   2. **Service Based**: one which utilizes specific protocols to communicate with open ports on a remote host, to determine more about the service that is running on that port
   3. **Banner Grabbing**: process of connecting to a specific port and examining data returned from the remote host to identify the service/application bound to that port. Often in the connection process, software will provide an identification string which may include information such as the name of the application, or information about which specific version of the software is running
3. **Web Application Scanners**:
   1. **General application flaw scanners**: they start with the address of a website, web application or web-service. The scanner then crawls the site by following links and directory structures. After compiling a list a list of webpages, resources, services and/or other media offered, the scanner will perform tests, or audits against the results of the crawl
   2. **Directory Listening/Brute Forcing**: suppose there are directories available on the website that the crawler won't find by following links; without prior knowledge, provided by the user, the scanner has at least 2 different options
   3. **Web Server Version/Vulnerability Identification**
4. **Network Vulnerability Scanners/Specific Protocols**
   1. VPN
   2. Voice Network Scanners
   3. Manual Direct Connections
   4. Obfuscated

### Passive Analysis

1. **Metadata analysis**: looking at data that describe a file:
   1. Document author
   2. Company
   3. When the document was last saved
   4. When the document was created
2. **Traffic-monitoring**: connecting to an internal network and capturing data for offline analysis, route poisoning is excluded from this phase as these create noise on the network and can easily be detected.

### Validation

### Research

## Exploitation

## Post exploitation

## Reporting
