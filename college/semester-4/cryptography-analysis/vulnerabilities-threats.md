# Vulnerabilities and threats

- [Vulnerabilities and threats](#vulnerabilities-and-threats)
  - [Background](#background)
  - [Common Vulnerability Exposure](#common-vulnerability-exposure)
    - [Syntax](#syntax)
    - [CNA, Who are they?](#cna-who-are-they)
    - [CVE Different States](#cve-different-states)
  - [National Vulnerability Database](#national-vulnerability-database)
    - [Information on the reports](#information-on-the-reports)
    - [States](#states)
  - [Common Vulnerability Score System](#common-vulnerability-score-system)
    - [Metrics](#metrics)
      - [Base](#base)
        - [Exploitability](#exploitability)
        - [Impact](#impact)
        - [Scope](#scope)
      - [Temporal](#temporal)
        - [Exploit Code Maturity (E)](#exploit-code-maturity-e)
        - [Remediation Level (L)](#remediation-level-l)
        - [Report Confidence (RC)](#report-confidence-rc)
    - [Environmental](#environmental)

## Background

> **Bug**: An error, flaw or fault in the design, development or operation of computer software that causes to produce an incorrect or unexpected result, or to behave in unintended ways.
> **Vulnerability**: A weakness in the code (in fancy words _computational logic_) found in software and hardware components that when exploited, results in a negative impact to confidentiality, integrity, or availability. Mitigation of vulnerabilities might be done with patches, specification changes or deprecation.
> **Exposure**: An error that gives an attacker access to a system or network.

## Common Vulnerability Exposure

> List of publicly disclosed information security vulnerabilities and exposures.

Public register that collects:

- Concise description of the vulnerability
- State
- Type of generated problem
- Systems affected
- References

### Syntax

CVE reports are handled through identifiers, which follow the structure `CVE-YEAR-NUMBER`:

- Year: year in which the vulnerability was registered
- Number: indicates the the registered number of the vulnerability, minimal size is 4 digits, no upper bound

### CNA, Who are they?

CNA Numeration Authorities (CNA) are organizations that identify and distribute CVE numbers to researchers and providers for their inclusion on public announces of newly found vulnerabilities. CNAs include software providers, open source projects, coordination centers, research groups and bug bounty service providers.

### CVE Different States

1. Reserved: a CVE entry is marked reserved when it has been reserved for use by a CNA or security researcher, but the details of it are not yet populated. It can change state to being populated at any time based on a number of factors both internal and external to the CVE list
2. Published: the CVE entry is populated with details, these include a description and reference links regarding details of the CVE
3. Disputed: a CVE receives this tag when 1 party disagrees with another party's assertion that a particular issue in software is a vulnerability. In this cases CVE is making no determination as to which party is correct, instead they make note of this dispute and try to offer any public references that will better inform those trying to understand the facts of the issue
4. Reject: receives the tag that is not accepted as a CVE entry, it might get rejected for being a duplicate of another CVE entry, it being withdrawn by the original requester, it being assigned incorrectly, or some other administrative reason.

## National Vulnerability Database

> It is the US government repository of standards based vulnerability management data represented using the Security Content Automation Protocol (SCAP). This data enables automation of vulnerability management, security measurement and compliance. The NVD includes databases of security checklist references, security related software flaws, misconfigurations, product names and impact metrics.

### Information on the reports

- Vulnerability description: Includes a CVSS and a vector string
- Bibliography: extended documentation on the vulnerability, its proposed solution and available tools
- Common Weakness Enumeration (CWE): similar to a metric that measures the weaknesses in software that occur frequently and that facilitates its designation to the description
- Influence: software affected by the vulnerability. Provided by the Common Platform Enumeration (CPE).

### States

- Received: a CVE has recently been published to the CVE list and has been received by the NVD.
- Awaiting analysis: marked for analysis, normally once the CVE is on this state it will by analyzed within 24 hours.
- Undergoing analysis: currently being analyzed, this process results in a report with reference link tags, CVSS scores, CWE association and CPE applicability statements.
- Analyzed: analysis completed and all data associations made
  - Initial: used to show the first time analysis was performed
  - Modified: used to show that analysis was performed due to a modification to the CVE
  - Reanalysis: a new analysis has occurred, but was not due to a modification from an external source
- Modified: the CVE has been amended by a source. Analysis data supplied by the NVD may be no longer accurate due to these changes.
- Deferred: when a CVE is given this status the NVD does not plan to analyze (or reanalyze) the CVE due to resource or other concerns.
- Rejected: stored in the NVD, but do not show up in search results.

## Common Vulnerability Score System

> An open framework for communicating the characteristics and severity of software vulnerabilities.

### Metrics

#### Base

##### Exploitability

- Attack Vector: Shows how a vulnerability may be exploited
  - Local (L): Needs physical access to the vulnerable system or a local account
  - Adjacent Network (A): needs access to the broadcast or collision domain of the vulnerable system
  - Network (N): the vulnerable interface is working at layer 3 or above of the OSI Network stack, they are often referred to as remotely exploitable
- Attack (Access) complexity (AC): addresses how easy or difficult it is to exploit the discovered vulnerability
  - High (H): specialized conditions exist, such as race condition with a narrow window
  - Medium (M): there are additional requirements for the attack, such as a limit on the origin of the attack, or the system to be running with an un-common configuration
  - Low (L): there are no special conditions for exploiting the vulnerability
- Privileges required: describes the level of privileges an attacker must possess before successfully exploiting the vulnerability
  - High (H): requires privileges that provide significant control over the vulnerable component allowing access to component-wide settings and files
  - Low (L): requires basic privileges that provide basic user capabilities that could normally affect only settings and files owned by the user
  - None (N): does not require access to any settings or files of the vulnerable system
- User interaction: captures the requirement for a human user (other than the attacker) to participate in the successful compromise of the vulnerable component.
  - Required (R): exploitation of this vulnerability requires a user to take some action before the vulnerability can be exploited
  - None (N): the vulnerability can be exploited without the need of user interaction

##### Impact

- Confidentiality impact (C): refers to limiting information access and disclosure to only authorized users, as well as preventing access from non-authorized users.
  - High (H): total loss of confidentiality, resulting in all resources within the impacted component being divulged to the attacker
  - Low (L): some loss of confidentiality, access to some restricted information is obtained, but the attacker does not have control over what information is obtained
  - None (N): no loss of confidentiality
- Integrity impact: refers to the trustworthiness and veracity of the information
  - High (H): total loss of integrity, for example, the attacker is able to modify any/all files protected by the impacted component
  - Low (L): modification of data is possible, but the attacker does not have control over the consequence of a modification, or the amount of modification is limited
  - None (N): no loss of integrity
- Availability impact: refers to the accessibility of information resources
  - High (H): total loss of availability, resulting in the attacker being able to fully deny access to resources in the impacted component
  - Low (L): performance is reduced or there are interruptions in resource availability
  - None (N): there is no impact to availability within the impacted component

##### Scope

> Captures whether a vulnerability in one vulnerable component impact resources in components beyond its security scope

- Unchanged (U): can only affect resources managed by the same security authority
- Changed (C): can affect resources beyond the security scope managed by the security authority of the vulnerable component

#### Temporal

##### Exploit Code Maturity (E)

> measures the likelihood of the vulnerability being attacked, and is typically based on the current state of exploit techniques, exploit code availability, or active _in the wild_ exploitation.

- Not defined (X): assigning this value indicates there is insufficient information to choose one of the other values
- High (H): functional autonomous code exists, or no exploit is required and details are widely available
- Functional (F): functional exploit code is available, the code works in most situations where the vulnerability exists
- Proof-of-concept (P): proof-of-concept code is available, or an attack demonstration is not practical for most systems
- Unproven (U): no exploit code is available, or an exploit is theoretical

##### Remediation Level (L)

> an important factor for prioritization, the typical vulnerability is unpatched when initially published

- Not defined (X): there is insufficient information to assign any of the other values
- Unavailable (U): there is either no solution available or it is impossible to apply
- Workaround (W): there is an unofficial, non-vendor solution available
- Temporary Fix (T): there is an official but _temporary_ fix
- Official Fix (O): a complete vendor solution is available

##### Report Confidence (RC)

> the degree of confidence in the existence of the vulnerability and the credibility of the known technical details

- Not defined (X): there is insufficient information to choose any of the other values
- Confirmed (C): detailed report exists, or functional reproduction is possible
- Reasonable (R): significant details are published, but researchers either do not have full confidence in the root cause, or do not have access to source code to fully confirm all of the interactions that may lead to the result
- Unknown (U): there are reports of impacts that indicate a vulnerability is present, the reports indicate that the cause of vulnerability is unknown, or reports may differ on the cause or impacts of the vulnerability

### Environmental

- Confidentiality requirement
- Integrity requirement
- Availability requirement
- Modified attack vector
- Modified attack complexity
- Modified privileges required
- Modified user interaction
- Modified scope
- Modified confidentiality
- Modified integrity
- Modified

For more info please refer back to [this website](https://en.wikipedia.org/wiki/Common_Vulnerability_Scoring_System) or [this page](https://www.first.org/cvss/specification-document)
