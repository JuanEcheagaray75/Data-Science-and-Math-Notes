# Operating systems security

- [Operating systems security](#operating-systems-security)
  - [Hardening](#hardening)
    - [Attack Surface](#attack-surface)
    - [Hardening practices](#hardening-practices)
    - [Benefits of systems hardening](#benefits-of-systems-hardening)
  - [OS Taxonomy](#os-taxonomy)
    - [By type of usage](#by-type-of-usage)
    - [By family](#by-family)
    - [By Kernel](#by-kernel)
    - [By multiple characteristics](#by-multiple-characteristics)
  - [Virtual Machines and Cloud Computing](#virtual-machines-and-cloud-computing)
    - [Cloud computing](#cloud-computing)
  - [Least privilege](#least-privilege)

## Hardening

> A collection of tools, techniques, and best practices to reduce vulnerability in technology applications, systems, infrastructure, firmware, and other areas. The goal of systems hardening is to reduce security risk by eliminating potential attack vectors and _condensing_ the system's attack surface. By removing superfluous programs, accounts functions, applications, ports permissions, access, etc... attackers and malware hace fewer opportunities to gain a foothold  within an IT ecosystem.

Hardening must be applied in different environments such as:

- Applications
- Operating Systems
- Servers
- Databases
- Networks

### Attack Surface

> The combination of all the potential flaws and backdoors in technology that can be exploited by hackers. These vulnerabilities can occur in multiple ways including:

- Default and hardcoded passwords
- Passwords and other credentials stored in plaintext files
- Unpatched software and firmware vulnerabilities
- Poorly configured BIOS, firewalls, ports, servers, switches, routers, or other parts of the infrastructure
- Unencrypted network traffic or data at rest
- Lack, or deficiency, of privileged access controls

### Hardening practices

- Audit your existing systems
- Create a strategy for systems hardening
- Patch vulnerabilities immediately
- Network hardening
  - Ensure your firewall is properly configured
  - Secure remote access points and end users
  - Block any unused or unneeded ports
  - Disable and remove unnecessary protocols and services
  - Implement access lists
  - Encrypt network traffic
- Server hardening
  - Put all servers in a secure data center
  - **Never** test hardening on production servers
  - Always harden servers before connecting them to the internet or external networks
  - Avoid installing unnecessary software
  - Segregate your servers
  - Ensure superuser and administrative shares are properly setup
- Application hardening
  - Remove components/functions you do not need
  - Restrict access based on user roles and context
  - Remove all sample files and default passwords
  - Passwords should be managed via a **password manager** app
  - Inspect integration with other applications and systems
- Database hardening
  - Create admin restrictions
  - Turn on node checking to verify application and users
  - **Encrypt** database information
  - Introduce Role-based access control (RBAC)
  - Remove unused accounts
- Operating system hardening
  - Apply OS updates, service packs and patches automatically
  - Remove unnecessary drivers, file sharing, libraries, software, services and functionality
  - Encrypt local storage
  - Tighten registry and other system permissions
  - **Log all activity**
  - Implement privileged user controls
- Eliminate unnecessary accounts and privileges
  - Enforce **least privilege** by removing unnecessary accounts  and privileges throughout your IT infrastructure

### Benefits of systems hardening

- Enhanced system functionality: since there are fewer programs and less functionality, there is less risk of operational issues, misconfigurations, incompatibilities and compromise
- Significantly improved security: a reduced attack surface translates into a lower risk of data breaches, unauthorized access, systems hacking, or malware
- Simplified compliance and auditability: fewer programs and accounts coupled with a less complex environment means auditing the environment will usually be more transparent and straightforward

## OS Taxonomy

> System software that manages computer hardware, software resources, and provides common services for computer programs

### By type of usage

- OS for network and server applications
- High performance
- Mobile devices
- Personal use

### By family

- Windows
- Linux
- Mac OS
- BSD
- Solaris
- UNIX
- Chrome/Android

### By Kernel

> A kernel is a computer program that is the heart and core of an OS. Whenever a system starts, the kernel is the first program that is loaded after the bootloader because the kernel has to handle the rest of the thing of the OS. It is responsible for low-level tasks such as disk management, memory management, tasks management, etc...

- Monolithic: where the user services and the kernel services are implemented in the same memory space. The size of the kernel is increased, and this in turn, increments the size of the OS. Since there is no separate space between User Space and Kernel, execution processes will tend to be faster
- Microkernel: the user services and kernel services are implemented into different spaces, reduces both kernel and OS sizes, the communication between application and services is done with the help of message parsing, which reduces execution speed.

### By multiple characteristics

- Multiuser: more than one user can use the OS at the same time
- Multiprocessing: can support the execution of multiple processes at the same time, it uses multiple number of CPUs
- Multiprogramming: more than one program can be used at the same time
- Multitasking: more than one task can be performed at the same time, but they are executed one after another through a single CPU by time sharing
- Multithreading: a program in execution is known as a process, a process can be further divided into multiple sub-processes, these are known as threads. A multithreading OS can divide a process into threads to increase speed at the cost of complexity
- Batch processing: a group of processing systems in which all the required input of all the processing tasks is provided initially, the result of all the tasks is provided after the completion of all the processing
- Online processing: an individual processing system in which the task is processed on individual basis as soon as they are provided by the user

## Virtual Machines and Cloud Computing

Operating systems can not be just mounted on physical devices, they can also be mounted on _virtual_ machines. To virtualize operating systems we often rely on one of the following apps:

- VMWare
- Virtual Box
- Xen
- Parallel Desktop

Some of the advantages of virtualization are:

- Resource optimization: you can mount several VMs on a physical machine
- Controlled environments: in case we perform a dangerous task, we'd rather do it on a VM

In cybersecurity, the usage of VM directly translates to:

- Controlled environments in which we can investigate how malicious code works
- They can be used as honey nets to catch hackers

### Cloud computing

> Where different companies offer VMs stored on the cloud

Cloud computing brings the next advantages:

- Save resources
- Have backups
- Suitable for online work

Evidently, for this advantages to hold, cloud computing infrastructure must comply with the characteristic of **availability**. The most common solutions are:

- Microsoft Azure
- Amazon Web Services (AWS)
- Oracle
- Google Cloud

But we don't need to get all fancy and acquire credits for a big tech VM, we can launch them from USB drives!, this feature allows us to:

- Test another OS without it being a VM, accompanied with the fact that we don't need to actually install the OS on the host machine
- Being able to do maintenance and information rescue tasks in case the host computer has been damaged.

## Least privilege

> The concept and practice of restricting access rights for users, accounts, and computing processes to only those resources absolutely required to perform routine, legitimate activities.

We hope to reduce privileges oriented towards:

- Applications
- Files
- Databases
- Services

With the **Principle of Least Privilege** we hope to:

- Prevent insider attacks
- Prevent unauthorized access
- To quarantine threats
