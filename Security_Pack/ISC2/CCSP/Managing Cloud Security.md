**Foundational Concepts and Business Requirements**

**Architectural Concepts**

Cloud Characteristics:

- Broad network access
- On-demand self-service
- Resource pooling
- Rapid elasticity
- Measured or “metered” service

Nist 800-145 Cloud Computing Definition:

- Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.
- These characteristics are also similar to how cloud computing is defined in ISO 17788.

**Broad network access:** Services are consistently accessible by standard means, such as the use of a web browser to access a SaaS application regardless of the user’s location or choice of computer OS, browser, and so on. This is generally accomplished with the use of such technologies as advanced routing techniques, load balancers, and multisite hosting, among others.

**On-demand self-service:** The model that allows customers to scale their compute and/or storage needs with little or no intervention from or prior communication with the provider. The services happen in real time.

**Resource pooling:** The characteristic that allows the cloud provider to meet various demands from customers while remaining financially viable. The cloud provider can make capital investments that greatly exceed what any single customer could provide on their own and can apportion these resources as needed so that the resources are not under-utilized (which would mean a wasteful investment) or overtaxed (which would mean a decrease in level of service). This is often referred to as a **multitenant environment;** multiple customers share the same underlying hardware, software and networking assets.

**Rapid elasticity:** Allows the customer to grow or shrink the IT footprint (number of users, number of machines, size of storage, and so on) as necessary to meet operational needs without excess capacity. In the cloud, this can be done in moments, as opposed to the traditional environment, where acquisition and deployment of resources (or dispensing old resources) can take weeks or months.

**Measured or “metered” service:** The customer is charged for only what they use and nothing more.

**Functional Requirements:** Those performance aspects of a device, process, or employee that are necessary for the business task to be accomplished.

**Nonfunctional requirements:** Those aspects of a device, process, or employee that are not necessary for accomplishing a business task but are desired or expected.

**Existing State**

**Methods for gathering business requirements:**

- Interviewing functional managers
- Interviewing users
- Interviewing senior management
- Surveying customers
- Collecting network traffic
- Inventorying assets
- Collecting financial records
- Collecting insurance records
- Collecting marketing data
- Collecting regulatory mandates

After sufficient data has been collected, a detailed analysis is necessary. This is the point where a **business impact analysis (BIA)** takes place.

**BIA:** An assessment of the priorities given to each asset and process within the organization.

\*\*Assets can be tangible or intangible. They can include hardware, software, intellectual property, personnel, processes, and so on. An example of tangible assets would be things like routers and servers, whereas intangible assets are generally something you cannot touch, such as software code, expressions of ideas, and business methodologies.\*\*

**Quantifying Benefits and Opportunity Cost**

Reduction in Capital Expenditure

- With a paid service (such as cloud), an operational expenditure, the entire payment (perhaps monthly or quarterly) is tax deductible as an expense.
- In the cloud, the organization is only paying for what it uses (regardless of the number of devices, or fractions of devices, necessary to handle the load), and no more.
  - This is a metered service.
  - As a result, the organization does not overpay for assets.
- Cloud providers have excess capacity available to be apportioned to cloud customers, so the organization is always in a position to experience increased demand and not be overwhelmed.
  - This is rapid elasticity.
- An organization can use hosted cloud services to augment internal, private data center capabilities with managed services during times of increased demand.
  - This is called **cloud bursting.** 
  - The organization might have data center assets it owns, but it can’t handle the increased demand during times of elevated need (crisis situations, heavy holiday shopping periods, and so on), so it rents the additional capacity as needed from an external cloud provider.

Reduction in Personnel Costs

- For most organizations (other than those that deliver IT services), managing data is not a core competency, much less a profitable line of business.
- Data management is also a specialized skill, and people with IT experience and training are relatively expensive (compared to employees in other departments).
- The personnel required to fulfill the needs of an internal IT environment represent a significant and disproportionally large investment for the organization.
- In moving to the cloud, the organization can largely divest itself of a large percentage, if not a majority, of these personnel.

Reduction in Operational Costs

- When an organization moves to the cloud, the cost becomes part of the price of the service, as calculated by the cloud provider.
- Therefore, costs are lumped in with the flat-rate cost of the contract and will not increase in response to enhanced operations (scheduled updates, emergency response activities, and so on).


Transferring Some Regulatory Costs

- Some cloud providers may offer holistic, targeted regulatory compliance packages for their customers.
- For instance, the cloud provider might have a set of controls that can be applied to a given customer’s cloud environment to ensure the mandates of **Payment Card Industry (PCI)** are met.
- In this manner, the cloud customer can decrease some of the effort and expense they might otherwise incur in trying to come up with a control framework for adhering to the relevant regulations.

\*\*Under current laws, no cloud customer can transfer risk or liability associated with the inadvertent or malicious disclosure of **personally identifiable information (PII).**\*\*

Reduction in Costs for Data Archival/Backup Services

- Off-site backups are standard practice for both long-term data archival and disaster recovery purposes.
- Having a cloud-based service for this purpose is sensible and cost-efficient even if the organization does not conduct its regular operations in the cloud.
- Moving operations into the cloud can create an economy of scale when combined with the archiving/backup usage; this can lead to an overall cost savings for the organization.
- It can enhance the **business continuity/disaster recovery (BC/DR) strategy** for the organization as well.

**Return on investment (ROI):** Term used to describe a profitability ratio. It is generally calculated by dividing net profit by net assets.

**Cloud Evolution, Vernacular, and Models**

Several characteristics are emblematic of cloud computing:

- **Elasticity:** Cloud provider uses virtualization to flexibly allocate only the needed usage of each resource to the organization, thus holding down costs while maintaining profitability. This also allows users to access their data from diverse platforms and locations, increasing portability, accessibility, and availability.
- **Simplicity:** Proper cloud implementations allow a user to seamlessly use the service without frequently interacting with the cloud service provider.
- **Scalability:** In general, increasing or reducing services can be more easily, quickly, and cost-effectively accomplished than in a non-cloud environment.

**Cloud customer:** Anyone purchasing a cloud service

**Cloud user:** Someone using cloud services.

Cloud Service Models

- Software as a Service (SaaS)
  - Applications
  - CRM
  - Hosted HR
  - Email
- Platform as a Service (PaaS)
  - Operating Systems
    - Windows
    - Linux
    - Unix
    - etc.
- Infrastructure as a Service (IaaS)
  - Hardware
  - Blades
  - Connectivity
  - Utilities

**Infrastructure as a Service (IaaS)**

The most basic of cloud service offerings, IaaS allows the customer to install all software, including OSs, on hardware housed and connected by the cloud vendor. In this model, the cloud provider has a data center with racks, machines, cables, and utilities and administers all these things. All logical resources, such as software, are the responsibility of the customer.

In traditional terms, we might think of this as what used to be considered a “warm site” for BC/DR purposes: the physical space exists, the connectivity exists, and it is available for the customer organization to fill with any type of baseline configuration and populate any data the customer requires.

Usually the least expensive cloud option, in terms of what the customer pays the provider. However, the customer will retain certain capabilities and requirements, such as IT staffing, that may make it difficult to ascertain the true total overall cost.




**Platform as a Service (PaaS)**

Contains everything included in IaaS with the addition of OSs. The cloud vendor usually offers a selection of OSs so that the customer can use any or all of the available choices. The vendor will be responsible for patching, administering, and updating the OS as necessary, and the customer can install any software they deem useful.

PaaS also includes cloud-based database engines and services as well as “big data”-style services, such as data warehousing and data mining. The provider offers access to the backend engine/functionality, while the customer can create/install various apps/APIs to access the backend.

**Software as a Service (SaaS)**

Includes everything in IaaS and PaaS with the addition of software programs. The cloud vendor becomes responsible for administering, patching, and updating this software as well. The cloud customer is basically only involved in uploading and processing data on a full production environment hosted by the provider.

The provider takes care of all the infrastructure, compute, and storage needs as well as providing the underlying operating systems and the application itself. All of this is completely transparent to the end user, who only sees the application they have purchased/accessed.

**Cloud Deployment Models**

**Public**

- The resources (hardware, software, facilities, and staff) are owned and operated by a vendor and sold, leased, or rented to anyone (offered to the public).
- Public clouds are **multi tenant environments**; multiple customers will share the underlying resources that are owned and operated by the provider.
- Examples
  - Rackspace
  - Microsoft’s Azure
  - Amazon Web Services (AWS)

**Private**

- Resources are dedicated to a single customer; no other customers will share the underlying resources (hardware and perhaps software).
- Not multi tenant environments.

**Community**

- Features infrastructure and processing owned and operated by (or for) an affinity group; disparate pieces might be owned or controlled by individuals or distinct organizations, but they come together in some fashion to perform joint tasks and functions.
- Can be provisioned by a third party on behalf of the various members of the community.

**Hybrid**

- Contains elements of the other models.

**Cloud Computing Roles and Responsibilities**

**Cloud Service Provider (CSP), or cloud Provider or Provider:** The vendor offering cloud services. The CSP will own the data center, employ the staff, own and manage the resources (hardware or software), monitor service provision and security, and provide administrative assistance for the customer and the customer’s data and processing needs.

**Cloud Customer:** The organization purchasing, leasing, or renting cloud services.

**Cloud Broker:** A company that purchases hosting services from a cloud provider who then resells them to its own customers.

**Cloud Access Security Broker (CASB):** A third-party entity offering independent identity and access management (IAM) services to CSPs and cloud customers, often as an intermediary.

**Regulators:** The entities that ensure organizations are in compliance with the regulatory framework for which they’re responsible. These can be government agencies, certification bodies, or parties to a contract.

**Cloud Computing Definitions**

- **Business requirement:** An operational driver for decision-making and input for risk management.
- **Cloud App (Cloud Application):** The phrase used to describe a software application accessed via the Internet; may include an agent or applet installed locally on the user’s device.
- **Cloud Architect:** Subject matter expert for cloud computing infrastructure and deployment.
- **Cloud Backup:** Backing up data to a remote, cloud-based server. As a form of cloud storage, cloud backup data is stored in an accessible form from multiple distributed resources that make up a cloud.
- **Cloud Computing:** The use of computing, storage, and network resources with the capabilities of rapid elasticity, metered service, broad network access, and pooled resources.
- **Cloud Migration:** The process of transitioning all or part of a company’s data, applications, and services from on-site premises to the cloud, where the information can be provided over the Internet on an on-demand basis.
- **Cloud Portability:** The ability to move applications and associated data between one cloud provider and another or between legacy and cloud environments.
- **Cost-Benefit Analysis:** This is comparing the potential positive impact (such as profit, efficiency, market share, and so on) of a business decision to the potential negative impact (expense, detriment to production, risk, and so on) and weighing whether the two are equivalent or if the potential positive effect outweighs the potential negative. This is a business decision, not a security decision, and it is best made by managers or business analysts.
- **FIPS 140-2:** A NIST document that describes the process for accrediting and cryptosystems for use by the US federal government.
- **Managed Service Provider:** An IT service where the customer dictates both the technology and operational procedures, and an external party executes administration and operational support according to a contract. A managed service provider might maintain and administer a data center/network for an organization at the organization’s business location, or in the cloud.
- **Multitenant:** Multiple customers using the same public cloud (and often the same hosts, in a virtualized cloud environment).
- **NIST 800-53:** A guidance document with the primary goal of ensuring that appropriate security requirements and controls are applied to all US federal government information in information management systems.
- **Trusted Cloud Initiative (TCI) Model:** The TCI reference model is a guide for cloud providers, allowing them to create a holistic architecture (including the physical facility of the data center, the logical layout of the network, and the processes necessary to utilize both) that cloud customers can purchase and use with comfort and confidence.
- **Vendor Lock-in:** Vendor lock-in occurs in a situation where a customer may be unable to leave, migrate, or transfer to an alternate provider due to technical or nontechnical constraints.
- **Vendor Lock-out:** Vendor lock-out occurs when a customer is unable to recover or access their own data due to the cloud provider going into bankruptcy or otherwise leaving the market.

**Foundational Concepts of Cloud Computing**

**Sensitive Data**

- Each organization will have its own risk appetite and desire for confidentiality. No matter how each cloud customer makes their own determination for these aspects of their data, the cloud provider must offer some way for the customer to categorize data according to its sensitivity and sufficient controls to ensure these categories are protected accordingly.

**Virtualization**

- One of the technologies that has made cloud services a financially viable business model. Cloud providers can purchase and deploy a sufficient number of host devices for a respective number of customers and users without wasting capacity or letting resources go idle.

**Encryption**

- Offers a degree of assurance that nobody without authorization will be able to access your data in a meaningful way. You can encrypt your data before it reaches the cloud and only decrypt it as necessary.

**Auditing and Compliance**

- From a compliance perspective, service providers may be able to offer holistic solutions for organizations under a particular regulatory schema.
- Cloud providers are extremely reluctant to allow physical access to their facilities or to share network diagrams and lists of controls; maintaining confidentiality of these things enhances the provider’s overall security.
- Audits will require the cooperation of the cloud provider, and providers have thus far disallowed the requisite level of access for the purpose.
- Any organization considering clou emigration should confer with regulators in order to determine if migration will be allowed and/or if additional measures will be required to protect regulated data.

**Cloud Service Provider Contracts**

- The business arrangement between the cloud provider and the cloud customer will usually take the form of a contract, which will include a service-level agreement (SLA).




**Related and Emerging Technologies**

- **Machine learning and artificial intelligence (AI):** Refers to the concept of programs and machines being able to acquire, process, correlate, and interpret information and then apply that in various capabilities without needing direct input from users or programs.
- **Blockchain:** An open means of conveying value using encryption techniques and algorithms. It is often referred to as “cryptocurrency.” It is basically a transactional ledger, where all participants can view every transaction, thus making it extremely difficult to negatively affect the integrity of past transactions. Blockchain can be perceived as a cloud technology because each record (“block”) is distributed among all the participants, regardless of location, type of device, jurisdiction, and so forth in a distributed, or cloud-based manner.
- **Internet of Things (IoT):** Any product that has Internet connectivity is referred to as the Internet of Things (IoT). The distributed nature of these devices (and their connection to and placement in networks) lends them some cloud characteristics. Perhaps the most salient security aspect of IoT is that devices without proper security can be subverted and used in attacks.
- **Containers:** The logical segmentation of memory space in a device, creating two or more abstract areas that cannot interface directly. This is commonly seen in bring your own device (BYOD) environments where employees use their personal devices for work. The containers distinguish two distinct partitions-one for work functions/data and the other for personal functions/data. This gives the employer/data owner additional assurance that the data will not be accidentally or casually lost or stolen.
- **Quantum computing:** This is an emerging technology that could allow IT systems to operate beyond binary math. Instead of using the presence of electrons for calculations (where the electrons exist in one of two states: either present or not present), quantum computing may use subatomic characteristics (electron spin, charm, and so on) to offer computation on an exponentially larger scale. This accelerates the machine’s ability to perform calculations/operations dramatically. Such systems are beginning to emerge beyond the theoretical stage, although none are yet commercially available at the time of this writing.
- **Homomorphic encryption:** The theoretical phenomenon that would allow processing of encrypted material without needing to first decrypt it. If achieved, this could allow cloud customers to upload encrypted data to the cloud and still utilize the data, without ever sharing the encryption keys with the cloud provider, or having to otherwise accommodate decryption as part of the process. 



**Design Requirements**

**Business Requirements Analysis**

- An inventory of all assets
- A valuation of each asset
- A determination of critical paths, processes, and assets
- A clear understanding of risk appetite

**Inventory of Assets**

- Everything owned or controlled by the organization can be considered an asset.
- Assets can be tangible items, such as IT hardware, retail inventory, buildings, and vehicles.
- Assets can also be intangible, such as intellectual property, public perception, and goodwill with business partners and vendors.
- Personnel can also be considered assets, because of the skills, training, and productivity they provide to the organization.
- The first step in creating a good security program would be to perform a thorough, comprehensive inventory.

**Valuation of Assets**

- We need to be able to know which of the assets provide the intrinsic value of our organization and which support this value.
- We need to know the value of the assets we protect so we know how much time, money, and effort to expend to protect them.
- This is a process known as **business impact analysis (BIA).** We determine a value for every asset (usually in terms of money, but sometimes according to priority/rank, customer perception, or other measures), what it would cost the organization if we lost that asset (either temporarily or permanently), what it would cost to replace or repair that asset, and any alternate methods for dealing with that loss.
- Normally, the data owners will determine the value of the information under their control.
- Overvaluing assets is a risk when letting data owners assign value to their assets.

**Determination of Criticality**

- Once the inventory and valuation is complete, the BIA effort continues with a determination made by senior management regarding criticality.
- Criticality denotes those aspects of the organization without which the organization could not operate or exist.
- These could include tangible assets, intangible assets, specific business processes, data pathways, or even essential personnel.
- The security professional should have a good understanding of the overall mission and function of the organization in order to better serve and advise the organization in securing critical elements.
- Another function of the BIA process that can support the security effort is the identification of **single points of failure (SPOFs).**
- SPOFs, especially in critical paths, pose a significant risk to the organization and ought to be addressed as soon as they are identified. Like critical aspects, SPOFs can be caused by hardware, software, processes, or personnel.
- Methods for dealing with SPOFs include the following:
  - Adding redundancies so that if the SPOF goes out of service, a replacement is immediately available.
  - Creating alternative processes to take the place of SPOFs in times of outage.
  - Cross-training personnel so that they can fill many roles.
  - Consistently and thoroughly backing up data in a manner from which it can be easily and quickly restored.
  - Load sharing/balancing for the IT assets.

**Quantitative and Qualitative Risk Assessments**

Both methods typically employ a set of methods, principles, or rules for assessing risk. Qualitative risk assessments use nonnumerical categories that are relative in nature, such as high, medium, and low. Quantitative assessments use specific numerical values such as 1, 2, and 3.

**Risk Appetite**

Risk appetite is the level, amount, or type of risk that the organization finds acceptable. This varies from organization to organization, based on innumerable factors both internal and external, and can change over time.

Risk fundamentals:

- Risk is the likelihood an impact will be realized.
- Risk can be reduced but never eliminated.
- Organizations accept a level of risk that allows operations to continue in a successful manner.
- It is legal and defensible to accept risks higher than the norm, or greater than your competitors, except risks to health and human safety; these risks must be addressed to the industry standard or the regulatory scheme to which your organization adheres.

Organizations have four main ways to address risks:

- **Avoidance:** Leaving a business opportunity because the risk is simply too high and cannot be compensated for with adequate control mechanisms - a risk that exceeds the organization’s appetite.
- **Acceptance:** The risk falls within the organization’s risk appetite, so the organization continues operations without any additional efforts regarding the risk.
- **Transference:** The organization pays someone else to accept the risk, at a lower cost than the potential impact that would result from the risk being realized; this is usually in the form of insurance. This type of risk is often associated with things that have a low probability of occurring but a high impact should they occur.
- **Mitigation:** The organization takes steps to decrease the likelihood or the impact of the risk (and often both); this can take the form of controls/countermeasures and is usually where security practitioners are involved.

When we choose to mitigate risk by applying countermeasures and controls, the remaining, leftover risk is called **residual risk.** The task of the security program is to reduce residual risk until it falls within the acceptable level of risk according to the organization’s risk appetite.


















**Data Classification and Cloud Security**

The **data owner** is the organization that has collected or created the data, in general terms. From a cloud perspective, the cloud customer is usually the data owner. Many international treaties and frameworks refer to the data owner as the **data controller.**

The **data custodian** is any person or entity that is tasked with the daily maintenance and administration of the data. The custodian also has the role of applying the proper security controls and processes as directed by the data owner. Within an organization, the custodian might be a database administrator.

**Processing** is anything that can be done to data. The **data processor** is any organization or person who manipulates, stores, or moves the data on behalf of the data owner. From an international law perspective, the cloud provider is a data processor.

Essential points about the rights and responsibilities of data ownership and custody:

- Data processors do not necessarily all have direct relationships with data owners; processors can be third parties, or even further removed down the supply chain.
- Data owners remain legally responsible for all data they own. This is true even if data is compromised by a data processor several times removed from the data owner.
- Ownership, custody, rights, responsibilities, and liability are all relative to the dataset in question and therefore are only specific to that data in that circumstance. For instance, the cloud provider is usually the data processor for a cloud customer’s data, but the provider is the data owner for information that the provider collects and creates, such as the provider’s own customer list, asset inventory, and billing information.

The data owner will be identified in the **Create phase.** Many data security and management responsibilities require action on the part of the data owner at this point in the life cycle.

A **data flow diagram (DFD)** is extremely useful in systems/software engineering in order to establish functional requirements before selection of the technology takes place; this obviates the likelihood that a choice of platform or component will drive the business process instead of the other way around.

In a cloud-based environment, diagramming allows the cloud customer to determine where specific controls need to be added and which are already supported by the provider (as stated in the contract/terms of service) and can aid in the choice and implementation of controls as well.

**Data Categorization**

Way an organization might categorize data:

- **Regulatory Compliance:** Different business activities are governed by different regulations. The organization may want to create categories based on which regulations apply to a specific dataset. This might include the Gramm-Leach-Bliley Act (GLBA), Payment Card Industry (PCI), Sarbanes-Oxley (SOX), Health Insurance Portability an dAccountability Act (HIPAA), General Data Protection Regulation (GDPR), and/or various other forms of international, national, and local compliance.
- **Business Function:** The organization might want to have specific categories for different uses of data. Perhaps the data is tagged based on its use in billing, marketing, or operations.
- **Functional Unit:** Each department or office might have its own category and keep all data it controls within its own category.
- **By Project:** Some organizations might define datasets by the projects they are associated with as a means of creating discrete, compartmentalized projects.

**Data Classification**

Data classification is the responsibility of the data owner, takes place in the Create phase, and is assigned according to an overall organizational policy based on a specific characteristic of the given dataset.



Types of Classification:

- **Sensitivity:** This is the classification model used by the US military. Data is assigned a classification according to the sensitivity of the data, based on the negative impact an unauthorized disclosure would cause. In models of this kind, classification must be assigned to all data, even in the negative, so material that is not deemed to be sensitive must be assigned the “unclassified” label.
- **Jurisdiction:** The geophysical location of the source or storage point of the data might have significant bearing on how that data is treated and handled.
- **Criticality:** Data that is deemed critical to organizational survival might be classified in a manner distinct from trivial, basic operational data. The business impact analysis (BIA) helps determine which material would be classified this way.

**Data Mapping**

Data between organizations (or sometimes even between departments) must be normalized and translated so that it conforms in a way meaningful to both parties. This is referred to as **data mapping.** When used in the context of classification efforts, mapping is necessary so that data that is known as sensitive (and in need of protection) in one system/organization is recognized as such by the receiving system/organization so that those protections can continue. 

**Data Labeling**

Labels should indicate who the data owner is, usually in terms of the office or role instead of an individual name or identity. The label should take whatever form is necessary for it to be enduring, understandable, and consistent. 

Labels might include the following kinds of information:

- Date of creation
- Data of scheduled destruction/disposal
- Confidentiality level
- Handling directions
- Dissemination/distribution instructions
- Access limitations
- Source
- Jurisdiction
- Applicable regulation


**Data Discovery Methods**

Data discovery may refer to the organization attempting to create an initial inventory of data it owns or that the organization is involved in electronic discovery (**e-discovery,** the legal term for how electronic evidence is collected as part of an investigation or lawsuit), and it can also mean the modern use of data mining tools to discover trends and relations in the data already in the organization’s inventory.

**Data Analytics**

Current technological options provide additional options for finding and assigning types to data. In many cases, these modern tools create new data feeds from sets of data that already exist within the environment. These include the following:

- **Datamining:** The term for the family of activities from which the other options on this list derive. This kind of data analysis is an outgrowth of the possibilities offered by regular use of the cloud, also known as “big data.” 
- **Real-Time Analytics:** In some cases, tools can provide data mining functionality concurrently with data creation and use. These tools rely on automation and require efficiency to perform properly.
- **Agile Business Intelligence:** State-of-the-art data mining involves recursive, iterative tools and processes that can detect trends in trends and identify even more oblique patterns in historical and recent data.

**Structured vs. Unstructured Data**

Data that is sorted according to meaningful, discrete types and attributes, such as data in a database, is said to be **structured.** Unsorted data is considered **unstructured.** It is typically much easier to perform data discovery actions on structured data because that data is already situated and arranged.

**Jurisdictional Requirements**

**The United States:** The US offers strong protections for intellectual property. There is no singular, overarching federal privacy statute; instead, the US tends to address privacy with industry-specific legislation (GLBA for banking/insurance, HIPAA for medical care, and so forth) or with contractual obligations (PCI). Many strong, granular data breach notification laws exist that are enforced by states and localities (especially New York and California).

**Europe:** Europe provides good intellectual property protections. It has massive, exhaustive, comprehensive personal privacy protections, including the EU General Data Protection Regulation.

**Asia:** Asia has disparate levels of intellectual property protection. Data privacy protection levels differ greatly by country. With its Act on the Protection of Personal Information, Japan adheres to the EU model, and Singapore does the same. Other countries follow much-reduced guidance. China, for example, has a legal requirement that is the opposite of privacy: all IT traffic and communications in China must be accessible by the Chinese government.

**South/Central America:** South America and Central America have various intellectual property mechanisms. Most countries lack privacy protection frameworks, with the notable exception of Argentina, which with its Personal Data Protection Act is in direct correlation with the EU legislation.

**Australia/New Zealand:** Australia and New Zealand provide strong intellectual property protections and very strong privacy protections, with the Australian Privacy Act mapping directly to the EU statutes.

**Information Rights Management (IRM)**

Managing information in accordance with who has rights to it is part of IRM. The term DRM is also often used, sometimes taken to mean “digital rights management” or “data rights management.” Other terms used to convey similar meanings include ERM (enterprise rights management) and offshoots such as E-DRM)

The concept of “rights management” entails the use of specific controls that act in concert with or in addition to the organization’s other access control mechanisms to protect certain types of assets, usually at the file level.

**Intellectual Property Protections**

Intellectual property is that class of valuable belongings that are intangible; literally, assets of the mind.

**Copyright:** The legal protection for expressions of ideas. In the US, copyright is granted to anyone who first creates an expression of an idea. Copyright protects the tangible expression of an idea, not the form of an idea.

**Exceptions to Copyright - Fair Use:**

- **Academic Fair Use:** Instructors can make limited copies or presentations of copyrighted works for educational purposes.
- **Critique:** Portions of the work may be used in critical reviews, discussing or assessing its merit.
- **News Reporting:** Because an informed populace is essential to a free society, we have waived some intellectual property protections for reporting purposes.
- **Scholarly Research:** Similar to academic fair use, but among researchers instead of teachers and students.
- **Satire:** A mocking sendup of the work may be created using a significant portion of the original work.
- **Library Preservation:** Libraries and archives are allowed to make limited numbers of copies of original works in order to preserve the work itself.
- **Personal Backup:** Someone who has legally purchased a licensed work may make a single backup copy for themselves, for use if the original fails. This explicitly includes computer programs.
- **Versions for People with Physical Disabilities:** It is legal to make specialized copies of licensed works for use by someone with a disability.

Copyright infringement is usually dealt with as a civil case: the copyright owner has to bring a lawsuit against someone they believe has illegally copied or used their work. However, in some cases, demonstrated willful infringement can be investigated by the government as a criminal matter and often referred to as **piracy.**

**Trademarks:** Protection intended to be applied to specific words and graphics. Trademarks are representations of an organization, its brand. In order to have a trademark protected by law, it must be registered within a jurisdiction. Commonly, that is the US Patent and Trademark Office (USPTO), the federal entity for registering trademarks.

**Patents:** Issued by the USPTO. The legal mechanism for protecting intellectual property in the form of inventions, processes, materials, decorations, and plant life. Globally, prospective patent holders might apply to the World Intellectual Property Office (WIPO) for approval under the Patent Cooperation Treaty, which has 152 signatory member nations. If a patent is approved by the WIPO, the property protected by the patent will be recognized in each of the member countries.

**Trade Secrets:** Cannot be disclosed to the public, and efforts must be made to maintain secrecy in order to keep this legal protection. Anyone who tries to acquire trade secrets by theft or misappropriation can be sued in civil court, but they can also be prosecuted in federal court.

**IRM Tool Traits**

**Rudimentary Reference Checks:** The content itself can automatically check for proper usage or ownership.

**Online Reference Checks:** Checking the program online with a product key against an online database when the system connects to the Internet.

**Local Agent Checks:** The user installs a reference tool that checks the protected content against the user’s license.

**Presence of Licensed Media:** Some IRM tools require the presence of licensed media, such as disks, in the system while the content is being used.

**Support-Based Licensing:** Some IRM implementations are predicated on the need of continual support for content; this is particularly true of production software. Licensed software might be allowed ready access to updates and patches, while the vendor could prevent unlicensed versions from getting this type of support.

**Challenges Employing IRM in the Cloud:**

- **Replication Restrictions:** Because IRM often involves preventing unauthorized duplication, and the cloud necessitates creating, closing, and replicating virtualized host instances (including user-specific content stored locally on the virtual host), IRM might interfere with automatic resource allocation processes.
- **Jurisdictional Conflicts:** The cloud extends across boundaries and borders, often in a manner unknown or uncontrolled by the data owner, which can pose problems when intellectual property rights are restricted by locale.
- **Agent/Enterprise Conflicts:** IRM solutions that require local installation of software agents for enforcement purposes might not always function properly in the cloud environment, with virtualization engines, or with the various platforms used in a BYOD enterprise.
- **Mapping Identity and Access Management (IAM) and IRM:** Because of the extra layer of access control (often involving content-specific access control lists, or ACLs), the IRM IAM processes might conflict or not work properly with the enterprise/cloud IAM. A conflict is even more possible when cloud IAM functions are outsourced to a third party, such as a cloud access security broker (CASB).
- **API Conflicts:** Because the IRM tool is often incorporated into the content, usage of the material might not offer the same level of performance across different applications, such as content readers or media players.

IRM should provide the following functions, regardless of type of content or format:

- **Persistent Protection:** The IRM should follow the content it protects, regardless of where that content is located, whether it is a duplicate copy or the original file, or how it is being utilized. This protection should not be easy to circumvent.
- **Dynamic Policy Control:** The IRM tool should allow content creators and data owners to modify ACLs and permissions for the protected data under their control.
- **Automatic Expiration:** Because of the nature of some legal protections of intellectual property, a significant amount of digital content will not be protected in perpetuity. The IRM protections should cease when the legal protections cease. Conversely, licenses also expire; access and permissions for protected content should likewise expire, no matter where that content exists at the end of the license period.
- **Continuous Auditing:** The IRM should allow for comprehensive monitoring of the content’s use and access history.
- **Replication Restrictions:** Much of the purpose of IRM is to restrict illegal or unauthorized duplication of protected content. Therefore, IRM solutions should enforce these restrictions across the many forms of copying that exist, to include screen-scraping, printing, electronic duplication, email attachments, and so on.
- **Remote Rights Revocation:** The owner of the rights to specific intellectual property should have the ability to revoke those rights at any time; this capability might be used as a result of litigation or infringement.

**Data Retention**

**Retention Periods:** The retention period is the length of time that the organization should keep data. This usually refers to data that is being archived for long-term storage, that is, data not currently being used in the production environment. The retention period is often expressed in a number of years and is frequently set by regulation or legislation. Data retention periods can also be mandated or modified by contractual agreements.

**Applicable Regulation:** The retention period can be mandated by statute or contract; the retention policy should refer to all applicable regulatory guidance. This is especially true in cases where there is conflicting regulation; the policy should then also highlight any such disparity, and include mention of senior management’s decision for how to approach and resolve this conflict with the policy as an appropriate mechanism.

**Retention Formats:** The policy should contain a description of how the data is actually archived, that is, what type of media it is stored on and any handling specifications particular to the data.

**Data Classification:** Highly sensitive or regulated data may entail specific retention periods, by mandate or contract or best practice. The organization can use the classification level of data to determine how long specific data sets or types of data need to be retained. Conversely, the retention period, if mandated, should be considered when the organization crafts the classification policy as a means to describe/create classification levels.

**Archiving and Retrieval Procedures:** Stored data can be used to correct production errors, can serve as business continuity and disaster recovery (BC/DR) backups, and can be data mined for business intelligence purposes. 

**Monitoring, Maintenance, and Enforcement:** The policy should list, in detail, how often it will be reviewed and amended, by whom, consequences for failure to adhere to the policy, and which entity within the organization is responsible for enforcement.

**Legal Hold:** When an organization is notified that either a law enforcement/regulatory entity is commencing an investigation or a private entity is commencing litigation against the organization, the organization must suspend all relevant data destruction activities until the investigation/lawsuit has been fully resolved.

**Data Audit**

- Log review and analysis is not often a priority.
- Log review is mundane and repetitive.
- Log review requires someone both new to the field and experienced.
- The reviewer needs to have an understanding of the operation.

**Data Destruction/Disposal**

- **Physical Destruction of Media and Hardware:** Any hardware or portable media containing the data in question can be destroyed by burning, melting, impact, or industrial shredding. This is the preferred method of sanitization since the data is physically unrecoverable.
- **Degaussing:** This involves applying strong magnetic fields to the hardware and media where the data resides, effectively making them blank. It does not work with solid-state drives.
- **Overwriting:** Multiple passes of random characters are written to the storage areas where the data resides, with a final pass of all zeros or ones. This can be extremely time-consuming for large storage areas. This is also not an effective technique for solid-state drives, which are resistant to overwriting.
- **Crypto-Shredding (Cryptographic Erasure)\*\*:** This involves encrypting the data with a strong encryption engine and then taking the keys generated in that process, encrypting them with a different encryption engine, and destroying the resulting keys of the second round of encryption.

**Data Classification and Cloud Security**

**Cloud Data Lifecycle:**

- Create
- Store
- Use
- Share
- Archive
- Destroy

**Create**

Data will most often be created by users accessing the cloud remotely. Depending on the use case, the data might be created locally by users at their remote workstation and then uploaded to the cloud or it might be created in the cloud data center via remote manipulation of the data residing there.

**Data Created Remotely:** Data created by the user should be encrypted before uploading to the cloud. The cryptosystem used for this purpose should have a high work factor and be listed on the FIPS 140-2 list of approved crypto solutions. Good key management practices should also be implemented.

**Data Created within the Cloud:** Data created within the cloud via remote manipulation should be encrypted upon creation, to obviate unnecessary access or viewing by data center personnel. Key management should be performed according to best industry practices.


**Store:** Usually meant to refer to near-term storage (as opposed to the Archive phase, which is long-term storage). The store phase will happen as data is created. 

**Use**

Operations in the cloud environment will necessitate remote access, so those connections will all have to be secured, usually with an encrypted tunnel.

Users must be trained to understand the new risks that go along with cloud computing and how they will be expected to use the technology in a safe manner. Data owners should also be careful to restrict permissions for modifying and processing their data; users should be limited to those functions that they absolutely require in order to perform their assigned tasks.

On the provider side, secure use requires strong protections in the implementation of virtualization; the provider must ensure that data on a virtualized host can’t be read or detected by other virtual hosts on that same device. The provider will have to implement personnel and administrative controls so that data center personnel can’t access any raw customer data.

**Share**

If users can be anywhere on the planet, so can threats. Many of the same security controls implemented in prior phases will be useful here: encrypted files and communications, IRM solutions, and so forth. There also needs to be sharing restrictions based on jurisdiction; data may need to be limited or data may need to be prevented from being sent to certain locations in accordance with regulatory mandates. These restrictions can take the form of either export controls or import controls, so the security professional must be familiar with both for all regions where the organization’s data might be shared.

**Archive**

The phase for long-term storage. Cryptography will be an essential consideration. Key management is of utmost importance, because mismanaged keys can lead to additional exposure or to total loss of the data. If the keys are improperly stored (especially if they are stored alongside the data), there is an increased risk of loss; if keys are stored away from the data but not managed properly and lost, there will be no efficient means to recover the data.

**Elliptical curve cryptography:** Approach to public key cryptography that uses much smaller keys than traditional cryptography to provide the same level of security. ECC uses algebraic elliptical curves that result in much smaller keys that can provide the same level of safety as much larger ones used in traditional key cryptography.

Risks and Benefits of proper storage:

- Location
- Format
- Staff
- Procedure

**Destroy**

Cryptographic erasure (crypto shredding) is the only feasible and thorough means currently available for this purpose in the cloud environment.

**Volume Storage: File-Based Storage and Block Storage**

**File Storage (also file-level storage or file-based storage):** Data is stored and displayed just as with a file structure in the traditional environment, as files and folders, with all the same hierarchical and naming functions.

**Block Storage:** A blank volume that the customer or user can put anything into. Block storage might allow more flexibility and higher performance, but it requires a greater amount of administration and might entail installation of an OS or other app to store, sort, and retrieve the data. Block storage might be better suited for a volume and purpose that includes data of multiple types and kinds, such as enterprise backup services.

**Object-Based Storage:** Data is stored as objects, not as files or blocks. Objects include not only the actual production content, but metadata describing the content and object and a unique address identifier for locating that specific object across an entire storage space. Enhances the opportunity for indexing capabilities, data policy enforcement, DLP, and centralization of some data management functions.

**Databases:** Provide some sort of structure for stored data. Data will be arranged according to characteristics and elements in the data itself, including a specific trait required to file the data known as the primary key. Most often implemented with PaaS and SaaS.

**Content Delivery Network (CDN):** A form of data caching, usually near geophysical locations of high use/demand, for copies of data commonly requested by users. 

**Key Management**

- Level of protection
- Key recovery
- Key distribution
- Key revocation
- Key escrow
- Outsourcing key management

**Masking, Obfuscation, Anonymization, and Tokenization**: For certain uses in the cloud, it may be necessary to obscure actual data and instead use a representation of that data.

Reasons to do this:

- Test Environments
- Enforcing least privilege
- Secure remote access
- Randomization
- Hashing
- Shuffling
- Masking
- Nulls

**Tokenization:**

- A user creates a piece of data
- The data is run through a DLP/discovery tool, as an aid to determine whether the data is sensitive according to the organization's rules. If the data is deemed sensitive, the data is pushed to the tokenization database.
- The data is tokenized; the raw data is sent to the PII server, while a token representing the data is stored in the tokenization database. The token represents the raw data as a kind of logical address.
- Another user requests the data. This user must be stringently authenticated so the systems can determine if the user should be granted access to the data.
- If the user authenticates correctly, the request is put to the tokenization database.
- The tokenization database looks up the token of the requested data, then presents that token to the PII database. The raw data is not stored in the tokenization database.
- The PII database returns the raw data based on the token.
- The raw data is delivered to the requesting user.

**Security Information and Event Management (SIEM)**

- Centralize collection of log data
- Enhanced analysis capabilities
- Dashboarding
- Automated response

**Egress Monitoring (DLP)**

- Additional Security
- Policy enforcement
- Enhanced monitoring
- Regulatory compliance









**Security in the Cloud**

**Shared Cloud Platform Risks and Responsibilities**

**Cloud Computing Risks by Deployment Model**

**Private Cloud:**

- Personnel threats
- Natural disasters
- External attacks
- Regulatory noncompliance
- Malware

**Community Cloud:**

- Resiliency through shared ownership
- Shared costs
- No need for centralized administration for performance and monitoring

**Public Cloud:** Has much of the same risks as private cloud.



**Vendor Lock-In:**

- Ensure favorable contract terms for portability
- Avoid proprietary formats
- Ensure there are no physical limitations to moving
- Check for regulatory constraints

**Vendor Lock-out:**

- Provider longevity
- Core competency
- Jurisdictional suitability
- Supply chain dependencies
- Legislative environment

**Multi Tenant Environments:**

- Conflict of interest
- Escalation of privilege
- Information bleed
- Legal activity

**Hybrid Cloud:** A combination of any of the other models. Takes on the risks of each model.

**Infrastructure as a Service (IaaS)**

- Personnel threats
- External threats
- Lack of specific skill sets

**Platform as a Service (PaaS)**

- Interoperability issues
- Persistent backdoor
- Virtualization
- Resource sharing

**Software as a Service (SaaS)**

- Proprietary formats
- Virtualization
- Web application security

**Virtualization**

- Attacks on the hypervisor
- Guest escape
- Information bleed
- Data seizure

**Threats**

- Malware
- Internal threats
- External attackers
- Man-in-the-Middle Attacks
- Theft/loss of devices
- Regulatory violations
- Natural disasters
- Loss of policy control
- Loss of physical control
- Lack of Audit Access
- Rogue administrator
- Escalation of Privilege
- Contractual failure

**Disaster Recovery (DR) and Business Continuity (BC)**

**Cloud-Specific BIA Concerns**

- New dependencies
- Regulatory failure
- Data breach/inadvertent disclosure
- Vendor lock-in/lock-out

**Logical location of Backup Data/Systems**

- Private architecture, Cloud service as backup
- Cloud operations, Cloud Provider as backup
- Cloud Operations, Third-Party Cloud backup provider

**Declaration:** The cloud customer and provider must decide, prior to the contingency, who specifically will be authorized to make this decision and the explicit process for communicating when it has been made.

**Testing:** Ensuring everything is working as intended.



**Responsibilities in the Cloud**

**Foundations of Managed Services**


**Business Requirements**

**Cloud Provider Responsibilities**

**The Physical Plant**

- Secure hardware components
- Manage hardware configuration
- Set hardware to log events and incidents
- Determine compute component composition by customer need
- Configure secure remote administrative access

**Secure Logical Framework**

- Installation of virtual OSs
- Secure configuration of various virtualized elements


**Secure Networking**

- Firewalls
- IDS/IPS
- Honeypots
- Vulnerability assessments
- Communication Protection
  - Encryption
  - Virtual Private Networks (VPNs)
  - Strong Authentication































**Cloud Application Security**

**Forklifting:** Moving an entire application to the cloud without any significant changes.

Issues and challenges that developers and administrators face when migrating to the cloud:

- Multi-tenancy
- Third-party admins
- Deployment models (public, private, community, hybrid)
- Service models (IaaS, PaaS, SaaS)

**Common Cloud Application Deployment Pitfalls**

- On-premises apps do not always transfer (and vice versa)
- Poor documentation
- Not all apps are cloud ready
- Tenancy separation
- Use of secure, validated APIs

**Cloud-Secure software Development Lifecycle (SDLC)**

- Defining
- Designing
- Development
- Testing
- Secure Operations
- Disposal

**ISO/IEC 27034-1:** An overview of application security that introduces definitive concepts, principles, and processes involved in application security. In doing so, it describes two documents an organization can use internally as inventories of controls.

**Identity and Access Management (IAM)**

**Identity Management:** The process whereby individuals are given access to system resources by associating user rights with a given identity. 

- Provisioning: Each subject is issued a unique identity assertion. During this process, the user is usually also issued a password for use in authenticating the identity assertion.



**Access Management:**

- Authentication
- Authorization
- Policy Management
- Federation
- Identity repositories

**Identity Repositories and Directory Services**

- X.500 and LDAP
- Microsoft Active Directory
- Novell eDirectory
- Metadata replication and synchronization

**Federation Standards**

- WS-Federation: Uses the term **realms** in explaining its capabilities to allow organizations to trust each other’s identity information across organizations.
- OAuth: Often used in authorization with mobile apps, the OAuth framework provides third-party applications limited access to HTTP services.
- OpenID Connect: An interoperable authentication protocol based on the OAuth 2 specification. It allows developers to authenticate their users across websites and applications without having to manage usernames and passwords.

**Application Programming Interfaces**

- RESTful APIs - Representational State Transfer: Software approach designed to scale the capabilities of web-based applications. 
- Characteristics of he REST API
  - Low processing/traffic overhead (“lightweight”)
  - Uses simple URLs/URIs
  - Not reliant on any single programming language
  - Scalable
  - Offers outputs in many formats
  - Efficient, which means it uses smaller messages than alternative approaches, such as SOAP
- Situations in which REST works well
  - When bandwidth is limited
  - When stateless operations are used
  - When caching is needed
- SOAP API - Simple Object Access Protocol: Protocol specification providing for the exchange of structured information or data in web services. It also works over other protocols such as SMTP, FTP, and HTTP.
- Characteristics of SOAP
  - Standards-based
  - Reliant on XML
  - Highly intolerant of errors
  - Slower
  - Built-in error handling
- Situations in which SOAP works or fits in better
  - Asynchronous processing
  - Format contracts
  - Stateful operations

**Cloud Application Assurance and Validation**

Types of threat modeling tools:

- Trike
- AS/NZS 4360
- CVSS

**STRIDE**

- Spoofing
- Tampering
- Repudiation
- Information Disclosure
- Denial of Service
- Elevation of privilege

Threat modeling helps prepare for some of the more common application vulnerabilities that developers will encounter when working with cloud applications, which include the following:

- Injection
- Broken Authentication
- Cross-site scripting (XSS)
- Insecure direct object access
- Security misconfigurations
- Sensitive data exposure
- Missing function-level access control
- Cross-site request forgery (CSRF)
- Using components with Known vulnerabilities
- Invalidated redirects and forwards

**Software Security Testing**

**White-Box testing (Static Application Security Testing [SAST]):** SAST entails reviewing the source code. 

Requires a testing team with two kinds of skills and knowledge:

- How to read the code the program was written with
- A deep understanding of security 

Be careful not to use the same person who wrote the code to perform testing.

**Black-Box Testing (Dynamic Application Security Testing [DAST]):** DAST entails testing the program as it functions, in runtime. The source code is not reviewed; instead, the testing team uses inputs and results from the application itself, as it’s running.











**Operations Elements**

**Holistic Redundancy: The Uptime Institute Tiers**

The Uptime Institute is an advisory organization for matters related to IT service. UI publishes a standard for data center design, and it also certifies data centers for compliance with this standard.

The UI standard is split into four tiers, in ascending durability of the data center. The standard itself is available for download from the UI’s website, free of charge.

**Tier 1**

A tier 1 data center is simplistic, with little or no redundancy, and is labeled Basic Site Infrastructure. Tier 1 lists the minimum requirements for a data center, which must include:

- Dedicated space for IT systems
- An uninterruptible power supply (UPS) system for line conditioning and backup purposes.
- Sufficient cooling systems to serve all critical equipment
- A power generator for extended electrical outages, with at least 12 hours of fuel to run the generator at sufficient load to power the IT systems.

Tier 1 data centers also have these features:

- Scheduled maintenance will require systems to be taken offline.
- Both planned and unplanned maintenance and response activity may take systems offline.
- Untoward personnel activity will result in downtime.
- Annual maintenance is necessary to safely operate the data center and requires full shutdown. Without this maintenance, the data center is likely to suffer increased outages and disruptions.

**Tier 2**

A tier 2 data center is named for its defining characteristics, Redundant Site Infrastructure Capacity Components. It features all the attributes of Tier 1, with these additional elements:

- Critical operations do not have to be interrupted for scheduled replacement and maintenance of any of the redundant components; however, there may be downtime for any disconnection of power distribution systems and lines.
- Untoward activity may cause downtime.
- Unplanned failures of components or systems might result in downtime.

**Tier 3**

Known as a Concurrently Maintainable Site Infrastructure. The facility features both the redundant capacity components of a Tier 2 build and the added benefit of multiple distribution paths. Other characteristics of tier 3:

- There are dual power supplies for all IT systems
- Critical operations can continue even if any single component or power element is out of service for scheduled maintenance or replacement.
- Unplanned loss of a component may cause downtime, the loss of a single system will cause downtime.
- Planned maintenance will not necessarily result in downtime; however, the risk of downtime may be increased during this activity. This temporary elevated risk does not make the data center lose its tier 3 rating for the duration.

**Tier 4**

The Fault-tolerant site infrastructure is the premium data center offering. As the UI repeats in the description of this tier, each and every element and system of the facility has integral redundancy such that critical operations can survive both planned and unplanned downtime at the loss of any component or system. On top of having everything the other 3 tiers have, Tier 4 also includes:

- There is redundancy of both IT and electrical components, where the various multiple components are independent and physically separate from each other.
- Even after the loss of any facility infrastructure element, there will be sufficient power and cooling for critical operations.
- The loss of any single system, component, or distribution element will not affect critical operations.
- The facility will feature automatic response capabilities for infrastructure control systems such that the critical operations will not be affected by infrastructure failures.
- Any single loss, event, or personnel activity will not cause downtime of critical operations.
- Scheduled maintenance can be performed without affecting critical operations. However, while one set of assets is in the maintenance state, the data center may be at increased risk of failure due to an event affecting the alternate assets. During this temporary maintenance state, the facility does not lose its Tier 4 rating.

**Virtualization Operations**

- Personnel Isolation
- Hypervisor Hardening
- Instance Isolation
- Host Isolation

**Storage Operations**

- Clustered storage and coupling
- Volume vs. object

**Other Storage**

- Ephemeral storage
- Long-term storage
- Content-delivery network (CDN)

**Resiliency**

There are two general ways for creating data protection in a cloud storage cluster: RAID (redundant array of independent disks) and data dispersion.

In most RAID configurations, all data is stored across the various disks in a method known as **striping**. This allows data to be recovered in a more efficient manner because if one of the drives fails, the missing data can be filled in by the other drives.

Data dispersion is a similar technique, where data is sliced into “chunks” (sometimes referred to as “shards”) that are encrypted along with parity bits (called **erasure coding** in cloud data dispersion) and then written to various drives in the cloud cluster. The parity bits/erasure encoding allow for the recovery of partial data lost (stored on  one “drive” or device or storage area) by re-creating the lost data from the remaining data plus the parity bits/erasure code. Data dispersion can be seen as equivalent to creating a RAID array in a cloud environment. This technique is also referred to as **bit splitting.**









**Operations Management**

**Monitoring, Capacity, and Maintenance**

**Monitoring**

- OS logging
- Hardware monitoring
- Network monitoring

**Maintenance**

- All operational instances are removed from the system/device before entering maintenance mode.
- Prevent all new logins.
- Ensure logging is continued, and begin enhanced logging.

**Updates**

- Document how, when, and why the update was initiated
- Move the update through the change management process.

**Upgrades:** Replacing older elements with newer ones.

**Patch Management:** A variety of updates most commonly associated with software. Considerations for patching:

- Timing
- Implementation - Automated or Manual
- Dates

**Change and Configuration Management (CM)**

- Baselines
- Deviations and Exceptions
- Roles and Process
- Release Management


