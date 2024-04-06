**Domain 1**

The key techniques to create a cloud are **abstraction** and **orchestration**. We abstract the resources from the underlying physical infrastructure to create our pools, and use orchestration (and automation) to coordinate carving out and delivering a set of resources from the pools to the consumers.

The Cloud Security Alliance (CSA) uses the **NIST model for cloud computing** as its standard for defining cloud computing. The CSA also endorses the **ISO/IEC model** which is more in-depth, and additionally serves as a reference model.

- **Resource pooling** is the most fundamental characteristic, as discussed above. The provider abstracts resources and collects them into a pool, portions of which can be allocated to different consumers (typically based on policies).
- **Broad network access** means that all resources are available over a network, without any need for direct physical access; the network is not necessarily part of the service.
- **Rapid elasticity** allows consumers to expand or contract the resources they use from the pool (provisioning and deprovisioning), often completely automatically
- **Measured service** meters what is provided, to ensure that consumers only use what they are allotted, and, if necessary, to charge them for it.

**“SPI” tiers** is a term to reference the three service models SaaS, PaaS and IaaS.

All this is facilitated using **Application Programming Interfaces**. APIs are typically the underlying communications method for components within a cloud, some of which (or an entirely different set) are exposed to the cloud user to manage their resources and configurations. Most cloud APIs these days use **REST (Representational State Transfer),** which runs over the HTTP protocol, making it extremely well suited for Internet services.

In most cases, those APIs are both remotely accessible and wrapped into a web-based user interface. This combination is the cloud management plane, since consumers use it to manage and configure the cloud resources, such as launching virtual machines.

IaaS consists of a facility, hardware, an abstraction layer, an orchestration (core connectivity and delivery) layer to tie together the abstracted resources, and APIs to remotely manage the resources and deliver them to consumers.

A customer asks for an instance (virtual server) of a particular size and the cloud controller determines which server has the capacity and allocates an instance of the requested size.

PaaS adds an additional layer of integration with application development frameworks, middleware capabilities, and functions such as databases, messaging, and queuing. These services allow developers to build applications on the platform with programming languages and tools that are supported by the stack.  In PaaS the cloud user only sees the platform, not the underlying infrastructure.

At a high level, both cloud and traditional computing adhere to a **logical model**:

- **Infrastructure:** The core components of a computing system: compute, network, and storage. The foundation that everything else is built on. The moving parts. 
- **Metastructure:** The protocols and mechanisms that provide the interface between the infrastructure layer and the other layers. The glue that ties the technologies and enables management and configuration. 
- **Infostructure:** The data and information. Content in a database, file storage, etc. 
- **Applistructure:** The applications deployed in the cloud and the underlying application services used to build them. For example, Platform as a Service features like message queues, artificial intelligence analysis, or notification services.

The key difference between cloud and traditional computing is the metastructure. Cloud metastructure includes the management plane components, which are network-enabled and remotely accessible. Another key difference is that, in cloud, you tend to double up on each layer.

**Shared responsibility model** - a responsibility matrix that depends on the particular cloud provider and feature/product, the service model, and the deployment model

The **Consensus Assessments Initiative Questionnaire (CAIQ).** A standard template for cloud providers to document their security and compliance controls.

The **Cloud Controls Matrix (CCM),** which lists cloud security controls and maps them to multiple security and compliance standards. The CCM can also be used to document security responsibilities.

High-level process for managing cloud security:

- Identify necessary security and compliance requirements, and any existing controls.
- Select your cloud provider, service, and deployment models.
- Define the architecture.
- Assess the security controls.
- Identify control gaps.
- Design and implement controls to fill the gaps.
- Manage changes over time.

**Domain 2**

**Contracts**: The primary tool of governance is the contract between a cloud provider and a cloud customer (this is true for public and private cloud). The contract is your only guarantee of any level of service or commitment—assuming there is no breach of contract, which tosses everything into a legal scenario

**Supplier (cloud provider) Assessments**: These assessments are performed by the potential cloud customer using available information and allowed processes/techniques.

**Compliance reporting:** Compliance reporting includes all the documentation on a provider’s internal (i.e. self) and external compliance assessments. They are the reports from audits of controls, which an organization can perform themselves, a customer can perform on a provider (although this usually isn’t an option in cloud), or have performed by a trusted third party.

The **Cloud Security Alliance STAR Registry** is an assurance program and documentation registry for cloud provider assessments based on the CSA Cloud Controls Matrix and Consensus Assessments Initiative Questionnaire.

**Enterprise Risk Management (ERM)** is the overall management of risk for an organization. As with governance, the contract defines the roles and responsibilities for risk management between a cloud provider and a cloud customer.

**Risk tolerance** is the amount of risk that the leadership and stakeholders of an organization are willing to accept.

In the majority of cases, SaaS presents the most critical example of the need for a negotiated contract.

The likelihood of a fully negotiated contract is likely lower here than with either of the other service models. That’s because the core driver for most PaaS is to deliver a single capability with very high efficiency

**Domain 3**

In Australia, two key laws provide protection to consumers of cloud services: the Privacy Act of 1988 (Privacy Act) and the Australian Consumer Law (ACL). The ACL protects consumers from false or misleading contracts and poor conduct from providers, such as failed breach notifications.

China’s Cyber Security Law imposes a series of security obligations to operators of critical information infrastructure, including internal organization, training, data backup; emergency response requirements, security inspections and annual assessments of cyber security risks; and reporting to relevant authorities. In addition, the law includes a data localization provision, which requires that personal information and other important data be stored within the territories of the People’s Republic of China

In Japan, the Act on the Protection of Personal Information (APPI) requires the private sector to protect personal information and data securely. Beginning in September 2017, amendments to the APPI law will limit the ability to transfer personal data to third parties, with prior consent of the data subject generally being required to transfer data to a third party.

The Russian data protection laws contain significant restrictions on data processing. Since September 2015, companies are required to store personal data of Russian citizens within Russia.


The European Union (EU) adopted the General Data Protection Regulation (GDPR) in 2016, which is binding on all EU member states, as well as members of the European Economic Area (EEA).  The GDPR applies to the processing of personal data in the context of the activities of an establishment of a controller or processor in the EU/EEA, regardless of whether the processing takes place in the EU/EEA or not.  The processing of personal data is allowed only if (a) the data subject has freely given specific, informed and unambiguous indication of his/her consent to the processing of his/her personal data, or (b) the processing is authorized by a statutory provision.

When data or operations are transferred to a cloud, the responsibility for protecting and securing the data typically remains with the collector or custodian of that data, even if in some circumstances this responsibility may be shared with others. Even when it relies on a third party to host or process its data, the custodian of the data remains liable for any loss, damage, or misuse of the data. It is therefore prudent, and may be required by law or regulation, that the data custodian and the cloud provider enter into a formal written agreement that clearly defines the roles, the expectations of the parties, and the allocation of the many responsibilities that are attached to the data at stake.

Before entering into any contract, a critical part of due diligence must be to request and review all relevant aspects of the operations of the other party.  In most cases, the cloud customer will want to evaluate at least the applicable service level, end-user and legal agreements; privacy policies; security disclosures; and proof of compliance with applicable legal requirements.

In a cloud environment, a client may not be able to apply or use e-discovery tools that it uses in its own environment. Moreover, a client may not have the ability or administrative rights to search or access all the data hosted in the cloud.

In addition to data preservation obligations resulting from U.S. laws regarding e-discovery, companies need to be aware that data retention laws require covered entities to retain data for a certain period of time.

**Scope of Preservation**: A requesting party is entitled only to data hosted in the cloud that contains, or is reasonably calculated to lead to, relevant, probative information for the legal issue at hand. The party is not entitled to all the data in the cloud or in the application.

**Access and Bandwidth**: In most cases, a client’s access to its data in the cloud will be determined by its SLA.  In a related issue, a client’s right of access may provide them access to a full range of data, but not provide them the degree of functionality that would best assist them in a given situation.

Should a cloud service provider receive, from a third party, a request to provide information; this may be in the form of a subpoena, a warrant, or a court order in which access to the client data is demanded. The client may want to have the ability to fight the request for access in order to protect the confidentiality of their data. To this end, the cloud service agreement should require the cloud service provider to notify the customer that a subpoena was received and give the company time to fight the request for access.

**Domain 4**

**GRC**, for governance, risk, and compliance. Although very closely related with audits — which are a key mechanism to support, assure, and demonstrate compliance — there is more to compliance than audits.

Best practices/frameworks like CSA CCM

If an IaaS provider is PCI DSS-certified, the customer can build their own PCI-compliant service on that platform and the provider’s infrastructure and operations should be outside the customer’s assessment scope.

An **attestation** is a legal statement from a third party, which can be used as their statement of audit findings. Attestations are a key tool when evaluating and working with cloud providers since the cloud customer does not always get to perform their own assessments.

Depending on the audit standard, actual results may only be releasable under a nondisclosure agreement (NDA), which means customers will need to enter into a basic legal agreement before gaining access to attestations for risk assessments or other evaluative purposes. This is often due to legal or contractual requirements with the audit firm, not due to any attempts and obfuscation by the cloud provider.

**Artifacts** are the logs, documentation, and other materials needed for audits and compliance; they are the evidence to support compliance activities.

**Domain 5**

**Custodianship** refers to who is managing the data. If a customer gives you their personal information and you don’t have the rights to own it, you are merely the custodian. That means you can only use it in approved ways. If you use a public cloud provider, they, likewise, become the custodian of the data.

**Data/information governance** means ensuring that the use of data and information complies with organizational policies, standards, and strategy.

**Privacy** is a sum of regulatory requirements, contractual obligations, and commitments to customers.

**Information Management Policies**. These tie to classification and the cloud needs to be added if you have them. They should also cover the different SPI tiers, since sending data to a SaaS vendor versus building your own IaaS app is very different. You need to determine what is allowed to go where in the cloud? Which products and services? With what security requirements?



Functions that can be performed with the data, by a given actor:

- Read. View/read the data, including creating, copying, file transfers, dissemination, and other exchanges of information. 
- Process. Perform a transaction on the data; update it; use it in a business processing transaction, etc. 
- Store. Hold the data

An **actor** (person, application, or system/process, as opposed to the access device) performs each function in a location.

**Controls**: A control restricts a list of possible actions down to allowed actions.

**Domain 6:**

The three main aspects of BC/DR in the cloud are:

- Ensuring continuity and recovery within a given cloud provider
- Preparing for and managing cloud provider outages.
- Considering options for portability, in case you need to migrate providers or platforms.

Your application can be balanced across zones so that if an entire zone goes down your application still stays up.

The **management plane** refers to the interfaces for managing your assets in the cloud. If you deploy virtual machines on a virtual network the management plane is how you launch those machines and configure that network.

The management plane controls and configures the metastructure (defined in Domain 1), and is also part of the metastructure itself.  As a reminder, cloud computing is the act of taking physical assets (like networks and processors) and using them to build resource pools. **Metastructure** is the glue and guts to create, provision, and deprovision the pools. The management plane includes the interfaces for building and managing the cloud itself, but also the interfaces for cloud users to manage their own allocated resources of the cloud.

**APIs** and web consoles are the way the management plane is delivered. **Application Programming Interfaces** allow for programmatic management of the cloud. They are the glue that holds the cloud’s components together and enables their orchestration.

Cloud providers and platforms will also often offer Software Development Kits (SDKs) and Command Line Interfaces (CLIs) to make integrating with their APIs easier.

APIs are typically **REST** for cloud services, since REST is easy to implement across the Internet. REST APIs have become the standard for web-based services since they run over HTTP/S and thus work well across diverse environments

These can use a variety of authentication mechanisms, as there is no single standard for authentication in REST. HTTP request signing and **OAuth** are the most common.

All privileged user accounts should use multi-factor authentication (MFA). If possible, all cloud accounts (even individual user accounts) should use MFA.

**Perimeter security**: Protecting from attacks against the management plane’s components itself, such as the web and API servers. It includes both lower-level network defenses as well as higher-level defenses against application attacks

BC/DR must take a risk-based approach.

**Software-Defined Infrastructure** allows you to create an infrastructure template to configure all or some aspects of a cloud deployment. These templates are then translated natively by the cloud platform or into API calls that orchestrate the configuration.

**Infostructure**: Data synchronization is often one of the more difficult issues to manage across locations, even if the actual storage costs are manageable. T

**Applistructure:** The application assets like code, message queues, etc. When a cloud user builds their own cloud applications they’re usually built on top of IaaS and/or PaaS, so resiliency and recovery are inherently tied to those layers. But Applistructure includes the full range of everything in an application.

SaaS may often be the biggest provider outage concern, due to total reliance on the provider.

**Domain 7:**

In cloud computing there are two macro layers to infrastructure:

- The fundamental resources pooled together to create a cloud.
- The virtual/abstracted infrastructure managed by a cloud user.

We most commonly see at least three different networks which are isolated onto dedicated hardware since there is no functional or traffic overlap:

- The service network for communications between virtual machines and the Internet.
- The storage network to connect virtual storage to virtual machines.
- A management network for management and API traffic.

**Microsegmentation** (also sometimes referred to as **hypersegregation**) leverages virtual network topologies to run more, smaller, and more isolated networks without incurring additional hardware costs that historically make such models prohibitive.

One emerging architecture for hybrid cloud connectivity is **“bastion”** or **“transit”** virtual networks:

- The cloud user builds a dedicated virtual network for the hybrid connection and then peers any other networks through the designated bastion network.
- Second-level networks connect to the data center through the bastion network, but since they aren’t peered to each other they can’t talk to each other and are effectively segregated.

**Containers:** Containers are code execution environments that run within an operating system (for now), sharing and leveraging resources of that operating system. While a VM is a full abstraction of an operating system, a container is a constrained place to run segregated processes while still utilizing the kernel and other capabilities of the base OS.

**Platform-based workloads**: This is a more complex category that covers workloads running on a shared platform that aren’t virtual machines or containers, such as logic/procedures running on a shared database platform.

**Serverless computing:** Serverless is a broad category that refers to any situation where the cloud user doesn’t manage any of the underlying hardware or virtual machines, and just accesses exposed functions.

Auto-scaling and containers, by nature, work best when you run instances launched dynamically based on an image; those instances can be shut down when no longer needed for capacity without breaking an application stack. This is core to the elasticity of compute in the cloud.  We call these virtual machines **immutable**.

**Domain 8:**

Virtualization adds two new layers for security controls:

- Security of the virtualization technology itself, e.g., securing a hypervisor.
- Security controls for the virtual assets.

The primary security responsibilities of the cloud provider in compute virtualization are to:

- Isolation ensures that compute processes or memory in one virtual machine/container should not be visible to another.
- Securing the underlying infrastructure and the virtualization technology from external attack or internal misuse. This means using patched and up-to-date hypervisors that are properly configured and supported with processes to keep them up to date and secure over time.

The provider should disable packet sniffing or other metadata “leaks” that could expose data or configurations between tenants.

Tagging or other SDN-level metadata should also not be exposed outside the management plane or a compromised host could be used to span into the SDN itself

**Cloud overlay** networks are a special kind of WAN virtualization technology for created networks that span multiple “base” networks. For example, an overlay network could span physical and cloud locations or multiple cloud networks, perhaps even on different providers.



**Domain 9:**

The Incident Response Lifecycle is defined in the NIST 800-61rev2 document. It includes the following phases and major activities:

- Preparation: “Establishing an incident response capability so that the organization is ready to respond to incidents.”
- Detection and Analysis
- Containment, Eradication, Recovery: Taking systems offline. Considerations for data loss versus service availability.  Clean up compromised devices and restore systems to normal operation.
- Post-Mortem: What could have been done better?

When preparing for cloud incident response, here are some major considerations:

- SLAs and Governance
- IaaS/PaaS vs. SaaS
- “Cloud jump kit:” These are the tools needed to investigate in a remote location
- Architect the cloud environment for faster detection, investigation, and response

Cloud-based applications should leverage automation and orchestration to streamline and accelerate the response, including containment and recovery.

The SLA with each cloud service provider must guarantee support for the incident handling required for the effective execution of the enterprise incident response plan.

**Domain 10:**

An effective application security program domain is broken into the following major areas:

- The Secure Software Development Lifecycle (SSDLC): How cloud computing affects application security, from design to deployment.
- Design and Architecture: Trends in designing applications for cloud computing that affect and can even improve security
- DevOps and Continuous Integration/Continuous Deployment (CI/CD):  Brings new security considerations, and again, opportunities to improve security over more manual development and deployment patterns like waterfall.

The Secure Software Development Lifecycle (SSDLC):

- Secure Design and Development
- Secure Deployment
- Secure Operations



There are five main phases in secure application design and development:

- Training
- Define
- Design
- Develop
- Test

There are multiple kinds of application security tests that could be potentially integrated into development and deployment:

**Code Review:** Any application communication with the management plane (e.g., API calls to the cloud service, some of which can alter the infrastructure) should be scrutinized, especially early in the project. Aside from looking at the code itself, the security team can focus on ensuring that only the least privilege entitlements are enabled for that part of the application and then validate them with the management plane configuration.

**Unit testing, regression testing, and functional tests:** These are the standard tests used by developers in their normal processes.

**Static Application Security Testing (SAST):** On top of the normal range of tests, these should ideally incorporate checks on API calls to the cloud service.

**Dynamic Application Security Testing (DAST):** DAST tests running applications and includes tests such as web vulnerability testing and fuzzing

Vulnerability assessment can be integrated into CI/CD pipelines and implemented in cloud fairly easily.  The first is running full assessments against images or containers as part of the pipeline in a special testing area of the cloud.  The image is only approved for production deployments if it passes this test. We see a similar pattern used to test entire infrastructures by building a test environment using infrastructure as code.  In both cases production is tested less, or not at all, since it should be immutable and exactly resemble the test environment.

On some cloud platforms it may be possible to use built-in assessment and configuration management features. It may also be possible to automatically remediate unapproved changes, depending on the platform and the nature of the change.

The following trends offer opportunities to reduce common security issues:

**Segregation by default**: Applications can easily be run in their own isolated cloud environments.

**Immutable infrastructure:**

**Increased use of micro-services**: In cloud computing, it is easier to segregate out different services onto different servers (or containers)

**PaaS and “serverless” architectures**: With PaaS and “serverless” setups there is great potential for dramatically reducing the attack surface.

**Software-defined security**: Security teams can leverage all the same tools and technologies to automate many security operations, even integrating them with the application stack.

**Event driven security**: Certain cloud providers support event-driven code execution. In these cases, the management plane detects various activities which can in turn trigger code execution through a notification message, or via serverless hosted code. Security can define events for security actions and use the event-driven capabilities to trigger automated notification, assessment, remediation, or other security processes.

**Domain 11:**

Data security controls tend to fall into three buckets:

- Controlling what data goes into the cloud (and where).
- Protecting and managing the data in the cloud.
- Enforcing information lifecycle management security

**Database**: Cloud platforms and providers may support a variety of different kinds of databases, including existing commercial and open source options, as well as their own proprietary systems. Proprietary databases typically use their own APIs. Commercial or open source databases are hosted by the provider and typically use existing standards for connections. These can be relational or non-relational—the latter includes NoSQL and other key/value storage systems, or file system-based databases (e.g. HDFS).

**CASB**: Cloud Access and Security Brokers (also known as Cloud Security Gateways) discover internal use of cloud services using various mechanisms such as network monitoring, integrating with an existing network gateway or monitoring tool, or even by monitoring DNS queries. After discovering which services your users are connecting to, most of these products then offer monitoring of activity on approved services through API connections (when available) or inline interception (man in the middle monitoring). Many support DLP and other security alerting and even offer controls to better manage use of sensitive data in cloud services.

**URL filtering**: While not as robust as CASB a URL filter/web gateway may help you understand which cloud services your users are using (or trying to use).

**DLP**: If you monitor web traffic (and look inside SSL connections) a Data Loss Prevention (DLP) tool may also help detect data migrations to cloud services.

Most cloud provider APIs use Transport Layer Security (TLS) by default

.




Access controls should be implemented with a minimum of three layers:

- **Management plane**: These are your controls for managing access of users that directly access the cloud platform’s management plane.
- **Public and internal sharing controls**: If data is shared externally to the public or partners that don’t have direct access to the cloud platform, there will be a second layer of controls for this access.
- **Application level controls**: As you build your own applications on the cloud platform you will design and implement your own controls to manage access.

**Format Preserving Encryption** encrypts data with a key but also keeps the same structural format as tokenization.

There are three components of an encryption system: data, the encryption engine, and key management.

Volume storage encryption:

- Instance-managed encryption: The encryption engine runs within the instance, and the key is stored in the volume but protected by a passphrase or keypair. 
- Externally managed encryption: The encryption engine runs in the instance, but the keys are managed externally and

Object and file storage

- Client-side encryption: When object storage is used as the back-end for an application (including mobile applications), encrypt the data using an encryption engine embedded in the application or client. 
- Server-side encryption: Data is encrypted on the server (cloud) side after being transferred in. The cloud provider has access to the key and runs the encryption engine. 
- Proxy encryption: In this model, you connect the volume to a special instance or appliance/ software, and then connect your instance to the encryption instance. The proxy handles all crypto operations and may keep keys either onboard or externally.

Database encryption: Data is encrypted in the database using encryption that’s built in and is supported by a database platform like Transparent Database Encryption (TDE) or at the field level.

**Data Loss Prevention (DLP)** is typically a way to monitor and protect data that your employees access via monitoring local systems, web, email, and other traffic. It is not typically used within data centers, and thus is more applicable to SaaS than PaaS or IaaS.

- **Test data generation:** This is the creation of a database with non-sensitive test data based on a “real” database. It can use scrambling and other randomization techniques to create a data set that resembles the source in size and structure but lacks sensitive data. 
- **Dynamic masking**: Dynamic masking rewrites data on the fly, typically using a proxy mechanism, to mask all or part of data delivered to a user. 

**Domain 12:**

Identity and access management is always complicated. At the heart we are mapping some form of an entity (a person, system, piece of code, etc.) to a verifiable identity associated with various attributes (which can change based on current circumstances), and then making a decision on what they can or can’t do based on entitlements.

**Identifier**: the means by which an identity can be asserted. For digital identities this is often a cryptological token. In the real world it might be your passport.

**Attributes**: facets of an identity. Attributes can be relatively static (like an organizational unit) or highly dynamic (IP address, device being used, if the user authenticated with MFA, location, etc.).

**Persona**: the expression of an identity with attributes that indicates context. For example, a developer who logs into work and then connects to a cloud environment as a developer on a particular project. The identity is still the individual, and the persona is the individual in the context of that project.

**Access control**: restricting access to a resource. Access management is the process of managing access to the resources

**Federated Identity Management**: the process of asserting an identity across different systems or organizations. This is the key enabler of Single Sign On and also core to managing IAM.

**Authoritative source:** the “root” source of an identity, such as the directory server that manages employee identities.

**Identity Provider:** the source of the identity in federation.

**Relying Party:** the system that relies on an identity assertion from an identity provider.

Federation involves an identity provider making assertions to a relying party after building a trust relationship. At the heart are a series of cryptographic operations to build the trust relationship and exchange credentials. A practical example is a user logging in to their work network, which hosts a directory server for accounts. That user then opens a browser connection to a SaaS application. Instead of logging in, there are a series of behind-the-scenes operations, where the identity provider (the internal directory server) asserts the identity of the user, and that the user authenticated, as well as any attributes. The relying party trusts those assertions and logs the user in without the user entering any credentials. In fact, the relying party doesn’t even have a username or password for that user; it relies on the identity provider to assert successful authentication. To the user they simply go to the website for the SaaS application and are logged in, assuming they successfully authenticated with the internal directory.

Identity brokers handle federating between identity providers and relying parties.

Authentication is the responsibility of the identity provider.

**Domain 13:**

**Security as a Service (SecaaS)** providers offer security capabilities as a cloud service. This includes dedicated SecaaS providers, as well as packaged security features from general cloud-computing providers.

Security assessments are third-party or customer-driven audits of cloud services or assessments of on-premises systems via cloud-provided solutions.

There are three main categories of security assessments: 

- Traditional security/vulnerability assessments of assets that are deployed in the cloud (e.g. virtual machines/instances for patches and vulnerabilities) or on-premises. 
- Application security assessments, including SAST, DAST, and management of RASP. 
- Cloud platform assessment tools that connect directly with the cloud service over API to assess not merely the assets deployed in the cloud, but the cloud configuration as well.

**Security Information and Event Management (SIEM)** systems aggregate (via push or pull mechanisms) log and event data from virtual and real networks, applications, and systems. This information is then correlated and analyzed to provide real-time reporting on and alerting of information or events that may require intervention or other types of responses.

**Domain 14:**

Big data is high volume, high velocity, and/or high variety information assets that require new forms of processing to enable enhanced decision making, insight discovery and process optimization.

There are three common components of big data: Distributed data collection, Distributed storage and Distributed processing.

The **Internet of Things** is a blanket term for non-traditional computing devices used in the physical world that utilize Internet connectivity.  Fitness trackers, connected lightbulbs, medical devices, and beyond.

Serverless computing is the extensive use of certain PaaS capabilities to such a degree that all or some of an application stack runs in a cloud provider’s environment without any customer-managed operating systems, or even containers.
