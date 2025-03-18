### Threat Intelligence, Risk Assessment, and Incident Response
---
 * Many organizations differentiate between events and incidents. Events are typically defined as observable-events like an email or a file download. Incidents are often classified as a violation of a security policy, unauthorized use or access, denial of service, or other malicious actions that may cause harm.

- A key differences between a risk score and a vulnerability score is that a risk score includes organizational context, while a vulnerability score does not.

- If the header for a vulnerability includes a Microsoft security bulletin ID, it indicates that Microsoft released a patch for the vulnerability.

- Under the United States' Cyber Incident Reporting for Critical Infrastructure Act of 2022 (CIRCIA), a qualifying incident must be reported within 72 hours. Ransomware payments must be reported within 24 hours.

> [!important] NIST Special Publications (SP)
>  > [!info] 800-53
>  > Defines security and privacy controls for information systems (risk management framework)
>   
>  > [!info] 800-55 & 800-80
>  > Defines metrics for the development, selection, and prioritization of information security measures.
>   
>  > [!info] 800-61
>  > Outlines the four-phase incident response process.
>    
>  > [!info] 800-88
>  > Defines the three main types of media sanitization.
>  

> [!important] International Organization for Standardization (ISO)
> > [!info] 27001
> > Describes standard approach for setting up an information security management system.
> 
> > [!info] 27002
> > Goes into more detail on the specifics of information security controls.


#### Analysis and Reporting

* NIST defines root cause analysis (RCA) as: A principle-based, systems approach for the identification of underlying causes associated with a particular set of risks.
- **Root Cause Analysis is a four step process:**
	1. Identification and description of problems and events.
	2. Establish a timeline of events.
	3. Differentiate between events and causes.
	4. Document the RCA.

* **Five Stages of the Intelligence Cycle**
	1. Requirements gathering: In this stage, organizations assess past threats, what information could have mitigated past threats, what controls and processes could improve security posture, and define requirements.
	2. Threat data collection: In this stage, organizations collect threat intelligence data related to their requirements. 
	3. Threat data analysis: In this stage, organizations analyze the data collected in the threat data collection stage.
	4. Threat intelligence dissemination: In this stage, teams share information with stakeholders such as leadership and security operations. 
	5. Gathering feedback: In this stage, organizations collect feedback on the process to enable continuous improvement.

- **Quantitative Risk Assessment**
	1. Determine the asset value (AV) of the asset affected by the risk.
	2. Determine the likelihood that the risk will occur.
	3. Determine the amount of damage that will occur to the asset if the risk materializes.
	4. Calculate the single loss expectancy.
	5. Calculate the annualized loss expectancy.

* **Common elements in a vulnerability report:**
	- Vulnerability details
		- Details such as a CVE number and description.
	- Affected hosts
		- IP addresses and hostname of systems found to be vulnerable.
	- Risk score
		- Details the risk severity in the context of the organization.
	- Mitigation options
		- Ways to mitigate the vulnerability
	- Recurrence
		- How often the vulnerability has reoccurred.
	- Prioritization
		- Context that helps prioritize which vulnerabilities should be addressed first.

- **Typical elements of threat models include:**
	- Assessment of adversary capabilities that help ascertain what resources, skills, and intent threat actors have  
	- Attack surface assessment that details the entire attack surface a threat actor may attempt to compromise or exploit (e.g., systems, people, and infrastructure)
	- Listing attack vectors a threat actor can use to gain access 
	- Attack impact
	- Attack probability of success

- **Typical Steps to the Threat Hunting Process:** 
	1. Establishing a Hypothesis
	2. Profiling Threat Actors and Activities
	3. Threat Hunting Tactics
	4. Reducing the Attack Surface Area
	5. Bundling Critical Assets into Groups and Protection Zones
	6. Understanding, Assessing, and Addressing Attack Vectors or the Means By Which an Attack Can Be Conducted.

- **Incident Response Process Steps (DRMRRRL):**
	- Detection
	- Response
	- Mitigation
	- Reporting
	- Recovery
	- Remediation
	- Lessons Learned

- **Incident response metrics and KPIs (Key Performance Indicators):**
	- Time to detect - The amount of time between an event that triggered an incident occurring and the event being detected
	- Time to respond - The time between incident detection and response activity beginning
	- Time to remediate - How long it takes to remediate an issue; this metric is typically significantly more complex than time to detect or time to respond and requires more nuanced communications and explanations
	- Alert volume - The number of alerts associated with an incident

| **Stakeholder type**                      | **Description**                                             | **Relevant information examples**                                   |
| ----------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------- |
| Technical                                 | People doing technical work related to cybersecurity issues | Vulnerability details, remediation options, and issue priority      |
| Security, audit, and compliance           | People responsible for security posture and compliance      | Trends, recurring problems, and reports on overall security posture |
| Security management and oversight systems | Systems that ingest and enrich cybersecurity data           | Structured data, API responses, and reports                         |
| Executives and leadership                 | Business leaders.                                           | Dashboards and high-level summaries                                 |


#### Threat Identification and Classification

- <mark style="background: #FF5582A6;">CVSS Scoring mnemonics:</mark>
	- "4321 Rule":
		- Low Severity - CVSS Score 4
		- Medium Severity - CVSS Score 4 + 3
		- High Severity - CVSS Score 4 + 3 + 2
		- Critical Severity - CVSS Score 4 + 3 + 2 + 1
	- "A Very Agile Programmer Usually Solves Complex Issues Always":
		- `AV:/AC:/PR:/UI:/S:/C:/I:/A:/

- **Lockheed Martin's Cyber Kill Chain Seven Stages:**
	1. Reconnaissance - Targets are selected and researched.
	2. Weaponization - Tools for exploitation are created.
	3. Delivery - A weapon(s) is sent to a target (e.g., via email).
	4. Exploitation - A malicious program is executed.
	5. Installation - Backdoors or similar programs installed.
	6. Command-and-Control (C2) - The stage where the intruder has access to manipulate systems.
	7. Actions on Objectives - The intruder performs the activities they desire, such as exfiltrating data or damaging a system.

- **Microsoft's STRIDE Classification Model**
	- Spoofing of user identity
	- Tampering
	- Repudiation
	- Information disclosure
	- Denial of service
	- Elevation of privilege

- **Four Threat Categories Identified by NIST**
	- Adversarial threats that try to intentionally harm an organization.
	- Accidental threats which can occur when individuals make a mistake.
	- Structural threats which can occur when equipment, resources, software, or infrastructure fail or are depleted.
	- Environmental threats that stem from disasters (e.g., hurricanes, fires, or power outages).

| **Category**                       | **Description**                                                                                     | **Examples**                                                                                            |
| ---------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Configuration management           | Deals with proper configuration, hardening, and creating baseline configurations for systems        | - Changing default passwords<br>- Using configuration management tools like Ansible                     |
| Patching                           | Deals with applying upgrades to systems to address security issues and software bugs                | - Updating an operating system<br>- Communicating a maintenance window to apply a patch                 |
| Compensating controls              | Involves the use of security controls to address a vulnerability that can not be directly mitigated | - Using a web application firewall to protect against common threats<br>- Isolating a vulnerable system |
| Awareness, education, and training | Deals with educating and training staff on cybersecurity practices and principles                   | - Training all staff on common social engineering threats<br>- Running phishing simulations             |
| Changing business requirements     | Modifying business requirements to address a vulnerability                                          | - Changing a policy <br>- Updating a software requirements document                                     |

- Unauthorized use and detection mechanisms:

| **Unauthorized Use Type**  | **Data Logged**                                | **Location of Data**                                | **Analysis Tools**                                                                                       |
| :------------------------: | ---------------------------------------------- | --------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
|    Unauthorized access     | Authentication<br>User creation                | Authentication logs<br>User creation logs           | Central management<br>suite<br>SIM/SIEM                                                                  |
|    Unauthorized changes    | File creation<br>Settings changes              | System logs<br>Application logs<br>Monitoring tools | Central management<br>suite<br>SIM/SIEM<br>Files and directory<br>integrity checking<br>tools (Tripwire) |
| Unauthorized privilege use | Privilege use attempts<br>Privilege escalation | Security event logs<br>Application logs             | SIM/SIEM<br>Log analysis tools                                                                           |

#### Email Security
---
- Forwarded emails will *not* include the original headers, as these are placed in new "envelopes" to be sent to others.

* Email Security Options -> pg. 118
	- *DomainKeys Identified Mail (DKIM)* - Allows organizations to add content to messages to identify them as being from their domain. DKIM signs both the body of the message and elements of the header, helping to ensure that the message is actually from the organization it claims to be from. It adds a DKIM-Signature header, which can be checked against the public key that is stored in public DNS entries for DKIM-enabled organizations.
	- *Sender Policy Framework (SPF)* - An email authentication technique that allows organizations to publish a list of their authorized email servers. SPF records are added to the DNS information for your domain, and they specify which systems are allowed to send email from that domain. Systems not listed in SPF will be rejected.
		- SPF records in DNS are limited to 255 characters. This can make it tricky to use SPF for organizations that have a lot of email servers or that work with multiple external senders. In fact, SPF has a number of issues you can run into-you can read more about some of them at [DMARC Analyzer - SPF](https://www.dmarcanalyzer.com/spf).
	- *Domain-Based Message Authentication, Reporting, and Conformance (DMARC)* - A protocol that uses SPF and DKIM to determine whether an email message is authentic. Like SPF and DKIM, DMARC records are published in DNS, but unlike DKIM and SPF, DMARC can be used to determine if you should accept a message from a sender.
		- Using DMARC, you can choose to reject or quarantine messages that are not sent by a DMARC-supported sender.


### Secure Software Development 
---
#### **Software Development Lifecycle Comparison** 
##### *Waterfall*
- Waterfall methodology is a software development method where steps occur sequentially and one step is completed before the next begins. Since Waterfall is not highly responsive to changes and does not account for internal iterative work, it is typically recommended for development efforts that involve a fixed scope and a known timeframe for delivery and that are using a stable, well-understood technology platform. A typical waterfall approach to software development is:
	1. Gather requirements
	2. Analyze
	3. Design
	4. Implement
	5. Test
	6. Deploy

##### *Spiral*
-  Spiral is similar to waterfall, but it iterates through four stages (identification, design, build, and evaluation) multiple times. The spiral model heavily emphasizes risk assessment in software development.
	1. 1. Identification, or requirements gathering, which initially gathers business requirements, system requirements, and more detailed requirements for subsystems or modules as the process continues.
	2. ﻿﻿﻿Design, conceptual, architectural, logical, and sometimes physical or final design.
	3. ﻿﻿﻿Build, which produces an initial proof of concept and then further development releases until the final production build is produced.  
	4. Evaluation, which involves risk analysis for the development project intended to monitor the feasibility of delivering the software from a technical and managerial view-point, As the development cycle continues, this phase also involves customer testing and feedback to ensure customer acceptance.

##### *Agile*
- Agile is an iterative and incremental approach to software development. Agile development focuses on breaking work into small chunks and delivering working software frequently. It has less up-front planning than waterfall or spiral. 
	- Individuals and interactions are more important than processes and tools.
	- Working software is preferable to comprehensive documentation.
	- Customer collaboration replaces contract negotiation.
	- Responding to change is key, rather than following a plan.
	- Focus on adapting to needs rather than predicting them.
* Based on 12 principles:
		1.  Ensure customer satisfaction via early and continuous delivery of the software.
		2. - Deliver working software frequently (in weeks rather than months).
		3. Ensure daily cooperation between developers and businesspeople.
		4. Projects should be built around motivated individuals who get the support, trust, and environment they need to succeed.
		5. Face-to-face conversations are the most efficient way to convey information inside the development team.
		6. Progress is measured by having working software.
		7. Development should be done at a sustainable pace that can be maintained on an ongoing basis.
		8. Pay continuous attention to technical excellence and good design.
		9. Simplicity-the art of maximizing the amount of work not done— is essential.
		10. The best architectures, requirements, and designs emerge from self-organizing teams. 
		11. Teams should reflect on how to become more effective and then implement that behavior at regular intervals.
		12. Welcome changing requirements, even late in the development process.

- Agile has a number of specialized terms:
	- ***Backlogs*** are lists of features or tasks that are required to complete a project.
	- ***Planning poker*** is a tool for estimation and planning used in Agile development processes. Estimators are given cards with values for the amount of work required for a task. Estimators are asked to estimate, and each reveals their "bid" on the task. This is done until agreement is reached, with the goal to have estimators reach the same estimate through discussion.
	- ﻿﻿***Timeboxing***, a term that describes the use of timeboxes. Timeboxes are a previously agreed-on time that a person or team uses to work on a specific goal. This limits the time to work on a goal to the timeboxed time, rather than allowing work until completion. Once a timebox is over, the completed work is assessed to determine what needs to occur next.
	- ﻿﻿***User stories*** are collected to describe high-level user requirements. A user story might be "Users can change their password via the mobile app," which would provide direction for estimation and planning for an Agile work session.		
	- ﻿﻿***Velocity tracking*** is conducted by adding up the estimates for the current sprint's effort track, faster, or slower than expected.

##### *RAD (Rapid Application Development) pg. 317*
- RAD (Rapid Application Development) is an iterative process that does not have a planning phase at all and relies heavily on prototype creation.

### Information Security Policy Framework
---
#### Policies
---

Policies are high-level statements of management intent. Compliance with policies is mandatory. An information security policy will generally contain broad statements about cybersecurity objectives, including:

-  A statement of the importance of cybersecurity to the organization
- ﻿﻿Requirements that all staff and contracts take measures to protect the confidentiality, integrity, and availability of information and information systems
- ﻿﻿Statement on the ownership of information created and/or possessed by the organization
- ﻿﻿Designation of the chief information security officer (CISO) or other individual as the executive responsible for cybersecurity issues
- ﻿﻿Delegation of authority granting the CISO the ability to create standards, procedures, and guidelines that implement the policy

In many organizations, the process to create a policy is laborious and requires very high-level approval, often from the chief executive officer (CEO). Keeping policy statements at a high level provides the CISO with the flexibility to adapt and change specific security requirements with changes in the business and technology environments. For example, the five-page information security policy at the University of Notre Dame simply states that:

> [!quote] 
> *The Information Governance Committee will create handling standards for each Highly Sensitive data element. Data stewards may create standards for other data elements under their stewardship. These information handling standards will specify controls to manage risks to University information and related assets based on their classification. All individuals at the University are responsible for complying with these controls.*

By way of contrast, the federal government's Centers for Medicare & Medicaid Services (CMS) has a 95-page information security policy. This mammoth document contains incredibly detailed requirements, such as:

> [!quote] 
> *A record of all requests for monitoring must be maintained by the CMS CIO along with any other summary results or documentation produced during the period of monitoring. The record must also reflect the scope of the monitoring by documenting search terms and techniques. All information collected from monitoring must be controlled and protected with distribution limited to the individuals identified in the request for monitoring and other individuals specifically designated by the CMS information.*

This approach may meet the needs of CMS, but it is hard to imagine the long-term maintenance of that document. Lengthy security policies often quickly become outdated as are weary of continually publishing new versions of the policy.

Organizations commonly include the following documents in their information security policy library:
- ﻿﻿*Information security policy* that provides high-level authority and guidance for the security program.
- ﻿﻿*Acceptable use policy (AUP)* that provides network and system users with clear direction on permissible uses of information resources.
- ﻿﻿*Data ownership policy* that clearly states the ownership of information created or used by the organization.
- ﻿﻿*Data classification policy* that describes the classification structure used by the organization and the process used to properly assign classifications to data.
- ﻿﻿*Data retention policy* that outlines what information the organization will maintain and the length of time different categories of work product will be retained prior to destruction. 
* *Account management policy* that describes the account life cycle from provisioning through active use and decommissioning.
* *Password policy* that sets forth requirements for password length, complexity, reuse, and similar issues.
- ﻿﻿*Continuous monitoring policy* that describes the organization's approach to monitoring and informs employees that their activity is subject to monitoring in the workplace.
- ﻿﻿*Code of conduct/ethics* that describes expected behavior of employees and affiliates and serves as a backstop for situations not specifically addressed in policy.

As you read through the list, you may notice that some of the documents listed tend to conflict with our description of policies as high-level documents and seem to better fit the definition of a standard in the next section. That's a reasonable conclusion to draw. CompTIA specifically includes these items as elements of information security policy stand and many organizations would move some of them, such as password requirements, into standards documents.

#### Standards
---

Standards provide mandatory requirements describing how an organization will carry out its information security policies. These may include the specific configuration settings used for a common operating system, the controls that must be put in place for highly sensitive information, or any other security objective. Standards are typically approved at a lower organizational level than policies and, therefore, may change more regularly.

For example, the University of California at Berkeley maintains a detailed document titled the Minimum Security Standards for Electronic Information, available online [here](https://security.berkeley.edu/minimum-security-standards-electronic-information. This document divides information into four different data protection levels (DPLs), and then describes what controls are required, optional, or not required for data at different levels using a detailed matrix.

> [!note] Service Level Objectives
> Organizations that offer technology services to customers may define service level objectives (SLOs) that set formal expectations for service availability, data preservation, and other key requirements. For example, the organization might set an SLO that customer-facing systems have 99.999% (or "five nines") of uptime. This means that the system would average less than six minutes of downtime each year.
> 
> SLOs are documented in service level agreements (SLAs) that are formal documents typically included in customer contracts. SLAs may include penalties for vendors who fail to meet their SLOs, such as refunding a portion of the service's fees.

#### Procedures
---

Procedures are detailed, step-by-step processes that individuals and organizations must follow in specific circumstances. Similar to checklists, procedures ensure a consistent process for achieving a security objective. Organizations may create procedures for building new systems, releasing code to production environments, responding to security incidents, and many other tasks. Compliance with procedures is mandatory.

For example, Visa publishes a document titled [What to Do If Compromised](https://usa.visa.com/dam/VCOM/download/merchants/cisp-what-to-do-if-compromised.pdf) that lays out a mandatory process that merchants suspecting a credit card compromise must follow. Although the document doesn't contain the word procedure in the title, the introduction clearly states that the document "establishes procedures and timelines for reporting and responding to a suspected or confirmed Compromise Event." The document provides requirements covering the following areas of incident response:
* Notify Visa of the incident within three days.
- ﻿﻿Provide Visa with an initial investigation report.
- ﻿﻿Provide notice to other relevant parties.
* Provide exposed payment account data to Visa.
- ﻿﻿Conduct PCI forensic investigation.
- ﻿﻿Conduct independent investigation.
- ﻿﻿Preserve evidence.

Each of these sections provides detailed information on how Visa expects merchants to handle incident response activities, For example, the forensic investigation section describes the use of Payment Card Industry Forensic Investigators (PFI) and reads as follows:

* Upon discovery of an account data compromise, or receipt of an independent forensic investigation notification, an entity must:
	- ﻿﻿Engage a PFI (or sign a contract) within five (5) business days.
	- ﻿﻿Provide Visa with the initial forensic (i.e., preliminary) report within ten (10) business days from when the PFI is engaged (or the contract is signed).
	- ﻿﻿Provide Visa with a final forensic report within ten (10) business days of the completion of the review.

There's not much room for interpretation in this type of language. Visa is laying out a clear and mandatory procedure describing what actions the merchant must take, the type of investigator they should hire, and the timeline for completing different milestones.

Organizations commonly include the following procedures in their policy frameworks:
- ﻿﻿***Monitoring procedures*** that describe how the organization will perform security monitoring activities, including the possible use of continuous monitoring technology.
- ﻿﻿***Evidence production procedures*** that describe how the organization will respond to subpoenas, court orders, and other legitimate requests to produce digital evidence.
- ﻿﻿***Patching procedures*** that describe the frequency and process of applying patches to applications and systems under the organization's care.

Of course, cybersecurity teams may decide to include many other types of procedures in their frameworks, as dictated by the organization's operational needs.

#### Guidelines
---

Guidelines provide best practices and recommendations related to a given concept, technology, or task. Compliance with guidelines is not mandatory, and guidelines are offered in the spirit of providing helpful advice. That said, the "optionality" of guidelines may vary significantly depending on the organization's culture.

In April 2016, the chief information officer (CIO) of the state of Washington published a 25-page document providing guidelines on the use of electronic signatures by state agencies. The document is not designed to be obligatory but rather offers advice to agencies seeking to adopt electronic signature technology. The document begins with a purpose section that outlines three goals of the guideline:
1. ﻿﻿﻿Help agencies determine if, and to what extent, their agency will implement and rely on electronic records and electronic signatures.
2. ﻿﻿﻿Provide agencies with information they can use to establish policy or rule governing their use and acceptance of digital signatures.  
3. Provide direction to agencies for sharing of their policies with the Office of the Chief Information Officer (OCIO) pursuant to state law.

The first two stated objectives line up completely with the function of a guideline. Phrases like "help agencies determine" and "provide agencies with information" are common in guideline documents. There is nothing mandatory about them and, in fact, the guidelines explicitly state that Washington state law "does not mandate that any state agency accept or require electronic signatures or records."

The third objective might seem a little strange to include in a guideline. Phrases like "provide direction" are more commonly found in policies and procedures. Browsing through the document, the text relating to this objective is only a single paragraph within a 25-page document, reading:

> [!quote]
> *The Office of the Chief Information Officer maintains a page on the OCIO website listing links to individual agency electronic signature and record submission policies. As agencies publish their policies, the link and agency contact information should be emailed to the OCIO Policy Mailbox. The information will be added to the page within 5 working days. Agencies are responsible for notifying the OCIO if the information changes.*

Reading this paragraph, the text does appear to dearly outline a mandatory procedure and would not be appropriate in a guideline document that fits within the strict definition be the term. However, it is likely that the committee drafting this document thought it would be much more convenient to the reader to include this explanatory text in the related guideline father than drafting a separate procedure document for a fairly mundane and simple task.


### Federated Identity Management
---
Comparison of federated identity technologies:

|                                 | **SAML**                                                                                            | **OpenID**                                                                                                                   | **OAuth2**                                                                                                                       | **AD FS**                                                                                             |
| :-----------------------------: | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
|        **Authorization**        | Yes                                                                                                 | No                                                                                                                           | Yes                                                                                                                              | Yes                                                                                                   |
|       **Authentication**        | Yes                                                                                                 | Yes                                                                                                                          | Partial                                                                                                                          | Yes                                                                                                   |
| **Potential Security<br>Risks** | Message confidentiality.<br><br>Protocol usage and <br>processing risks.<br><br>Denial of service.  | Message confidentiaelity.<br><br>Redirect <br>manipulation.<br><br>Replay attacks.<br><br>CSRF/XSS attacks.<br><br>Phishing. | Message confidentiality.<br><br>Redirect <br>manipulation.<br><br>Authorization or<br>resource server <br>impersonation.<br><br> | Token attacks (replay, capture).                                                                      |
|         **Common Uses**         | Enterprise authentication<br>and authorization, <br>particularly in <br>Linux-centric environments. | Authentication.                                                                                                              | API and service <br>authorization.                                                                                               | Enterprise authentication<br>and authorization, <br>particularly in <br>Windows-centric environments. |

Three key roles when using federated identities are:
- IDP (Identity Provider): Provides identities, makes identity-related assertions to relying parties, and releases identity-related information to relying parties.
- RP (Relying Party) or Service Provider (SP): Provides services to federation members and securely handles user and IDP data. 
- Consumer: Is the user of services that may make decisions about identity attributes and provide information to validate identity claims made to an IDP.

#### AD FS Authentication Process
---
1. The user attempts to access an ADFS-enabled web application hosted by a resource partner.
2. ﻿﻿﻿The ADFS web agent on the partner's web server checks for the ADFS cookie; if it is there, access is granted. If the cookie is not there, the user is sent to the partner's ADFS server.
3. ﻿﻿﻿The resource partner's ADFS checks for an SAML token from the account partner, and if it's not found, ADFS performs home realm discovery.
4. ﻿﻿﻿Home realm discovery identifies the federation server associated with the user and then authenticates the user via that home realm.
5. ﻿﻿﻿The account partner then provides a security token with identity information in the form of claims, and sends the user back to the resource partner's ADFS server.
6. ﻿﻿﻿Validation then occurs normally and uses its trust policy to map the account partner claims to claims the web application supports.
7. ﻿﻿﻿A new SAML token is created by ADFS that contains the resource partner claims, and this cookie is stored on the user's computer. The user is then redirected to the web application, where the application can read the cookie and allow access supported by the claims.

- ADFS can be controlled using the ADFS MMC snap-in, `adfs.msc`. The ADFS console allows you to add resource partners and account partners, map partner claims, manage account stores, and configure web applications that support federation. Microsoft provides a useful overview of ADFS found [here.](http://msdn.microsoft.com/en-us/library/bb897402.aspx)

### OS Architecture
---
#### Windows Registry 
---
- Five main Root keys:

|         **Root Key**         | **Description**                                                              |
| :--------------------------: | ---------------------------------------------------------------------------- |
|  `HKEY_CLASSES_ROOT (HKCR)`  | COM object registration information. Associates files<br>type with programs. |
| `HKEY_LOCAL_MACHINE (HKLM)`  | System information, including scheduled tasks and <br>services.              |
|      `HKEY_USERS (HKU)`      | Information about user accounts.                                             |
|  `HKEY_CURRENT_USER (HKCU)`  | Information about the currently logged-in user.                              |
| `HKEY_CURRENT_CONFIG (HKCC)` | Current local hardware profile information storage.                          |

- Root key run locations:

|        **Root Key**         | **Run Key Location**                                                   |
| :-------------------------: | ---------------------------------------------------------------------- |
| `HKEY_LOCAL_MACHINE (HKLM)` | `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run`     |
|  `HKEY_CURRENT_USER (HKU)`  | `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`      |
| `HKEY_LOCAL_MACHINE (HKLM)` | `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce` |
|  `HKEY_CURRENT_USER (HKU)`  | `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce`  |

#### Windows System Processes
---

| **PID** | **Name**  | **Description**                                                         |
| :-----: | --------- | ----------------------------------------------------------------------- |
|    0    | IDLE      | Responsible for accounting IDLE time on system (not an actual process). |
|    4    | NT Kernel | Core system process, found in `C:\Windows\System32\notskrnl.exe`.       |

|  **Process**   | **Description**                                                           |
| :------------: | ------------------------------------------------------------------------- |
| `notskrnl.exe` | NT Kernel                                                                 |
|   `smss.exe`   | Session Manager Subsystem - responsible<br>for starting the user session. |
| `winlogon.exe` | Windows Logon Application - loads user<br>profile into the registry.      |

#### System Configuration Files Locations
---

| **OS**  | **Location**                                                                            |
| :-----: | --------------------------------------------------------------------------------------- |
| Windows | Windows Registry, `C:\ProgramData\` or `C:\Program Files\`, <br>or `AppData` directory. |
|  Linux  | Commonly stored in `/etc/`.                                                             |
|  macOS  | `~/Library/Preferences` and `/Library/Preferences`                                      |

#### Miscellaneous OS Architecture
---
- The default macOS drive format is Apple File System (APFS) and is the native macOS drive format. macOS does support FAT32 and can read New Technology File System (NTFS) but cannot write to NTFS drives without additional software. HFS+ was the default file system for earlier versions of macOS.

- The Windows Quick Format option leaves data in unallocated space on the new volume, allowing the data to be carved and retrieved. This does not meet the requirements for any of the three levels of sanitization defined by NIST.

- Shadow copies in Windows are block-level copies, and can be safely deleted.

### Networking
---
#### Network Architecture 

|         **Architecture**          | **Description**                                                                    | **Pros**                                                                                 | **Cons**                                                                                  |
| :-------------------------------: | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
|            On-Premises            | IT infrastructure that is hosted in-house and <br>managed by the organization.     | Full control over hardware and software; potentially better security and compliance.     | High upfront costs; requires in-house expertise; scalability can be limited.              |
|               Cloud               | IT resources and services delivered over the internet by a third-party provider.   | Scalability; cost-effective; reduced need for in-house IT management; high availability. | Dependency on internet connectivity; potential security and compliance concerns.          |
|              Hybrid               | Combination of on-premises and cloud services.                                     | Flexibility; optimized costs; improved disaster recovery and business continuity.        | Complexity in management; potential security risks; requires integration between systems. |
|       Network Segmentation        | Dividing a network into smaller segments to improve security and performance.      | Enhanced security; improved performance; easier management of network traffic.           | Complexity in setup and management; potential for misconfiguration.                       |
|            Zero Trust             | Security model that assumes no implicit trust and verifies every access request.   | Improved security posture; limits lateral movement of threats; granular access control.  | Can be complex to implement; may require significant changes to existing infrastructure.  |
| Secure Access Service Edge (SASE) | Converges networking and security functions into a single cloud-delivered service. | Simplified management; improved security; better performance for remote users.           | Relatively new concept; potential vendor lock-in; may require significant changes.        |
| Software-Defined Networking (SDN) | Approach to networking that uses software-based controllers to manage hardware.    | Centralized management; improved network agility and flexibility; easier automation.     | Initial setup complexity; potential security vulnerabilities; requires new skill sets.    |

- A bastion host is a server that's designed to withstand cyberattacks and provide secure access to a private network from an untrusted network, like the internet. 

#### Logging Levels
- Vary between vendors.
- Cisco Logging Levels:

| **Level** | **Level Name** | **Example**                         |
| :-------: | -------------- | ----------------------------------- |
|     0     | Emergencies    | Device shutdown due to <br>failure. |
|     1     | Alerts         | Temperature limit exceeded.         |
|     2     | Critical       | Software failure.                   |
|     3     | Errors         | Interface down message.             |
|     4     | Warning        | Configuration change.               |
|     5     | Notifications  | Line protocol up/down.              |
|     6     | Information    | ACL violation.                      |
|     7     | Debugging      | Debugging messages.                 |

#### Capturing Network-Related Events
- Three main methods: router-based monitoring, active monitoring, or passive monitoring.
- Note: both active and router-based traffic monitoring add traffic to the network, which means that the network monitoring systems may be competing with the traffic they are monitoring.
##### Router-Based Monitoring
- Tools: NetFlow, sFlow, J-Flow.
- Flows typically show the source, its IP address, the destination, its IP address, how many packets were sent, how much data was sent, and the port and protocol that was used.

##### Active Monitoring
- Typically gathers data about availability, routes, packet delay or loss, and bandwidth.
- Examples of active monitoring include:
	- **Pings**: ICMP packets to ping remote systems. Only provides basic up/down information. 
	- **iPerf**: A tool that measures the maximum bandwidth that an IP network can handle.
- Tools: Nagios.

##### Passive Monitoring
- Relies on capturing information about the network as traffic passes a location on a network link. Can allow the monitoring system to capture the traffic sent, providing a detailed view of the traffic's rate, protocol, and content, as well as packet sending and receiving performance.
- Unlike router-based and active monitoring, passive monitoring does not add additional traffic to the network. Also performs after-the-fact analysis, since the packets must be captured and analyzed, rather than being recorded in real-time as they were sent.

#### Miscellaneous Networking
---
- Objectives outline: bandwidth consumption, beaconing, irregular peer-to-peer communication, rogue devices, scans and sweeps, unusual traffic spikes, and activity on unexpected ports.

- *Baselines* or, *anomaly-based detection*, requires knowledge of what normal traffic is, where the baselines are typically gathered during normal network operations. Once baseline data is gathered, monitoring systems can be set to alarm when the baselines are exceeded by a given threshold or when network behavior deviates from the behaviors documented.
- *Heuristics*, or *behavior-based detection*, uses network security devices and defined rules for scans, sweeps, attack traffic, and other network issues.
- *Protocol analysis*, uses a protocol analyzer to captures packets and check for problems.

- 802.1X is an agent-based, out-of-band NAC implementation.

- Fast-flux DNS is when an attacker associates many IP addresses with a domain and quickly changes them. Blocking an IP address would not have much affect, because the attacker is quickly rotating between IP addresses. Blocking the domain entirely would help address exploits that leverage fast-flux DNS.

### Miscellaneous
---
- STIX (Structured Threat Information Expression) is a language based on XML used for threat intelligence data. Starting with STIX 2.0 JSON, STIX uses JSON instead of XML formatting.

- Contrary to what some believe, PCI DSS is not a law. The standard is maintained by an industry group known as the Payment Card Industry Security Standards Council (PCI SSC), which is funded by the industry to maintain the requirements. Organizations are subject to PCI DSS due to contractual requirements rather than by law.

* A load test tests an application to confirm it works under normal loads. 95–105% adequately represents this range. 

* Stress testing tests an application under loads that exceed normal conditions. 125–200% of normal load is a reasonable estimate for this this range, but it could go higher as the goal of stress testing is partially to determine when the application's performance begins to degrade.

- Credential stuffing occurs when an attacker uses known credentials from one service on other services. Password spraying attacks occur when an attacker uses common passwords to attempt logins to many different accounts.

### References
---
#### Blue Team
- [Windows Processes - An overview for Blue Teams](https://nasbench.medium.com/windows-system-processes-an-overview-for-blue-teams-42fa7a617920)
- [CISecurity Benchmark](https://www.cisecurity.org/benchmark)
- [Kubernetes Vulnerability Scanning](https://www.wiz.io/academy/kubernetes-vulnerability-scanning)
- [Privileged Access Management PAM](https://www.beyondtrust.com/resources/glosaary/privileged-access-management-pam)
- [Simulating a beacon](https://www.activecountermeasures.com/simulating-a-beacon)
- [SANS - Posters](https://www.sans.org/posters/)
- [TCPDump Examples](https://hackertarget.com/tcpdump-examples)
- [TCPDump](https://danielmiessler.com/study/tcpdump)
- [Understanding an Email Header](http://mediatemple.net/community/products/dv/204643950/understanding-an-email-header)
- [Email Header Breakdown](https://blog.mailfence.com/email-header)
- [Learn X in Y Minutes](https://learnxinyminutes.com/)
- [STIX & TAXII CTI Documentation](https://oasis-open.github.io/cti-documentation)
- [Using SLAs For Better Vulnerability Management](https://phoenix.security/using-slas-for-better-vulnerability-management-remediation-improving-developers-workflow/)
- [SAML Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SAML_Security_Cheat_Sheet.html)
- [Wazuh - Open Source Security Platform](http://wazuh.com)
- [MAC Vendors](https://www.macvendors.com)
- [MAC Vendor Lookup](https://www.macvendorlookup.com)

#### Threat Intelligence
- [Open Source Threat Intelligence Feeds](https://www.senki.org/operators-security-toolkit/open-source-threat-intelligence-feeds/)
- [AbuseIPDB](https://www.abuseipdb.com/)
- [Open Threat Intelligence](https://cybersecurity.att.com/open-threat-intelligence)
- [Misp Threat Sharing](https://www.misp-project.org/feeds)
- [Threat Feeds](https://threatfeeds.io)
- [AlienVault OTX Threat Intelligence Sharing](https://otx.alienvault.com/)
- [Talos Intelligence Reputation Center](https://talosintelligence.com/reputation_center) 
- [Threat Hunting Labs - Beacons](https://activecm.github.io/threat-hunting-labs/beacons/)
- [NIST National Software Reference Library - NSRL](https://www.nist.gov/itl/ssd/software-quality-group/national-software-reference-library-nsrl)

#### Malware Analysis 
- [Malware Analysis - malwr](https://www.malwr.co/)
- [Joesandbox](https://www.joesandbox.com)
- [Cuckoo Sandbox](https://www.cuckoosandbox.org)
- [Any.Run - Malware Sandbox](https://www.any.run)

#### Tools 
- Resource monitor (resmon)
- Performance monitor (perfmon)
- NetFlow
- sFlow
- J-Flow
- iPerf
- Tripwire
- Advanced Intrusion Detection Environment (AIDE)
- System Center Operations Manager (SCOM)
- Nagios
- [Kubernetes REK2](https://docs.rke2.io/)
- [Kubernetes K9 CLI](https://k9scli.io/#:~:text=K9s%20is%20a%20terminal%20based,interact%20with%20your%20observed%20resources)






