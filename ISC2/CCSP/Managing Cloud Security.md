## Domain 1: Cloud Computing Concepts and Architectures

### 1.1 Overview

**NIST Cloud Computing Definition:** A model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort or service provider interaction.
* **NIST 500-292:** Uses the term “cloud actor” and adds roles for cloud brokers, carriers, and auditors.
* **NIST 800-145:** Brings coherence and consensus around a common language to focus on use cases rather than semantic nuances.

**5 Essential Characteristics**
* **Broad Network Access:** All resources are available over a network, without any need for direct physical access; the network is not necessarily part of the service.
* **Rapid Elasticity:** Allows consumers to expand or contract the resources they use from the pool, often completely automatically. This allows consumers to closely match resource consumption with demand.
* **Measured Service:** 
* **On-Demand Self-Service:** Consumers provision resources from the pool themselves, without having to talk to a human administrator.
* **Resource Pooling:** Provider collects resources into a pool, then allocates portions to different consumers (typically based on policies).

**3 Service Models (SPI Tiers)**
* **Software as a Service (SaaS):** Full application that’s managed and hosted by the provider. Consumers access it with a web browser, mobile app, or a lightweight client app.
* **Platform as a Service (PaaS):** Abstracts and provides development or application platforms, such as databases, application platforms, file storage and collaboration, or proprietary application processing. With PaaS, the cloud provider manages the underlying servers, networks, or other infrastructure.
* **Infrastructure as a Service (IaaS):** Offers access to a resource pool of fundamental computing infrastructure, such as compute, network, or storage.

**4 Cloud Deployment Models**
* **Public:** The cloud infrastructure is made available to the general public or a large industry group and is owned by an organization selling cloud services.
  * **Infrastructure managed by:** Third-Party Provider
  * **Infrastructure owned by:** Third-Party Provider
  * **Infrastructure located:** Off-Premises
  * **Accessible and Consumed By:** Untrusted
* **Private:** The cloud infrastructure is operated solely for a single organization. It may be managed by the organization or by a third party and may be located on-premises or off-premises.
  * **Infrastructure managed by:** Organization/Third-Party Provider
  * **Infrastructure owned by:** Organization/Third-Party Provider
  * **Infrastructure located:** On-Premises/Off-Premises
  * **Accessible and Consumed By:** Trusted
* **Hybrid:** The cloud infrastructure is a composition of two or more clouds that remain unique entities but are bound together by standardized or proprietary technology that enable data and application portability. Hybrid is also commonly used to describe a non-cloud data center bridged directly to a cloud provider.
  * **Infrastructure managed by:** Both Organization and Third-Party Provider
  * **Infrastructure owned by:** Both Organization and Third-Party Provider
  * **Infrastructure located:** Both On-Premises and Off-Premises
  * **Accessible and Consumed By:** Trusted and Untrusted
Community: The cloud infrastructure is shared by several organizations and supports a specific community that has shared concerns. It may be managed by the organizations or by a third party and may be located on-premises or off-premises.
Infrastructure managed by: Organization/Third-Party Provider
Infrastructure owned by: Organization/Third-Party Provider
Infrastructure located: On-Premises/Off-Premises
Accessible and Consumed By: Trusted
ISO/IEC Cloud Computing Definition: Paradigm for enabling network access to a scalable and elastic pool of shareable physical or virtual resources with self-service provisioning and administration on-demand.
Cloud User (Client/Consumer): Person or organization requesting and using the resources
Cloud Provider (Service/Cloud): Person or organizations that delivers resources.
ISO/IEC 17788: Uses the terms cloud service customer, cloud service partner, and cloud service provider. Lists six key characteristics, the first five of which are identical to the NIST characteristics. The only addition is multi-tenancy, which is distinct from resource pooling.
ISO/IEC 17789: Cloud Reference Architecture
On top of IaaS, PaaS, and SaaS, ISO/IEC adds cloud services that are more granular, such as Compute as a Service orData Storage as a Service.
Clouds are multitenant. Multiple consumers share the same resources but are segregated and isolated from each other. 
Cloud Security Alliance (CSA): Uses the NIST model for cloud computing as its standard for defining cloud computing. The CSA also endorses the ISO/IEC model which is more in-depth, and additionally serves as a reference model.
Cloud Computing Stack
Software as a Service (SaaS)
Presentation modality
Presentation platform
APIs
Applications
Data
Metadata
Content
Platform as a Service (PaaS)
Integration and Middleware
Infrastructure as a Service (IaaS)
APIs
Core connectivity
Abstraction
Hardware
Facilities
Infrastructure as a Service (IaaS):
Application Programming Interfaces (APIs): Typically the underlying communications method for components within a cloud, sum of which are exposed to the cloud user to manage their resources and configurations. Most cloud APIs use Representational State Transfer (REST), which runs over HTTP protocol, making it extremely well suited for Internet services.
Cloud Management Plane: APIs that are both remotely accessible and wrapped into a web-based user interface. Consumers use it to manage and configure cloud resources. If an attacker gains access to the management plane, they potentially have full remote access to the entire cloud deployment.
IaaS consists of:
A facility
Hardware
An abstraction layer
An orchestration layer to tie together the abstracted resources
APIs to remotely manage the resources and deliver them to consumers
Platform as a Service (PaaS):
Adds an additional layer of integration with application development frameworks, middleware capabilities, and functions such as databases, messaging, and queuing.
The cloud user only sees the platform, not the underlying infrastructure.

Software as a Service (SaaS):
Full, multi-tenant applications, with all the architectural complexities of any large software platform.
Most use a combination of IaaS and PaaS, sometimes across different cloud providers.
Have an application/logic layer and data storage with an API on top. Then one or more presentation layers, including web browsers, mobile applications, and public API access.
Logical Model
Infrastructure: The core components of a computing system; compute, network and storage. The foundation that everything else is built on. The moving parts
Metastructure: The protocols and mechanisms that provide the interface between the infrastructure layer and the other layers. The glue that ties the technologies and enables management and configuration.
Infostructure: The data and information. Content in a database, file storage, etc.
Applicastructure: The applications deployed in the cloud and the underlying application services used to build them.
The key difference between cloud and traditional computing is the metastructure. Cloud metastructure includes the management plane components, which are network-enabled and remotely accessible. In the cloud, every layer tends to be doubled up on each layer.
1.2 Cloud Security Scope, Responsibilities, and Models



