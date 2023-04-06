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

**shared responsibility model** - a responsibility matrix that depends on the particular cloud provider and feature/product, the service model, and the deployment model

The **Consensus Assessments Initiative Questionnaire (CAIQ).** A standard template for cloud providers to document their security and compliance controls.

The **Cloud Controls Matrix (CCM),** which lists cloud security controls and maps them to multiple security and compliance standards. The CCM can also be used to document security responsibilities.

high-level process for managing cloud security:

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


















































