**Module 1: Cloud Concepts Overview**

**Section 1: Introduction to Cloud Computing**

**Cloud computing** is the on-demand delivery of compute power, database, storage, applications, and other IT resources via the internet with pay-as-you-go pricing.

Cloud computing enables you to stop thinking of your infrastructure as hardware, and instead think of (and use) it as software.

**Traditional Computing Model**

Infrastructure as hardware

Hardware solutions:

Require space, staff, physical security, planning, capital expenditure

Have a long hardware procurement cycle

Require you to provision capacity by guessing theoretical maximum peaks.

**Cloud Computing Model**

Infrastructure as software

Software solutions:

Are flexible

Can change more quickly, easily, and cost-effectively than hardware solutions

Eliminate the undifferentiated heavy-lifting tasks.

**Cloud Service Models**

IaaS - Infrastructure as a Service (More control over IT resources)

Services in this category are the basic building blocks for cloud IT and typically provide you with access to networking features, computers (virtual or on dedicated hardware), and data storage space. IaaS provides you with the highest level of flexibility and management control over your IT resources. It is the most similar to existing IT resources that many IT departments are familiar with today.

PaaS - Platform as a Service

Services in this category reduce the need for you to manage the underlying infrastructure (usually hardware and operating systems) and enable you to focus on the deployment and management of your applications.

SaaS - Software as a Service (Less control over IT resources)

Services in this category provide you with a completed product that the service provider runs and manages. In most cases, SaaS refers to end-user applications. With a SaaS offering, you do not have to think about how the service is maintained or how the underlying infrastructure is managed. You need to think only about how you plan to use that particular piece of software.



**Cloud Computing Deployment Models**

**Cloud:** A cloud-based application is fully deployed in the cloud, and all parts of the application run in the cloud. Applications in the cloud have either been created in the cloud or have been migrated from an existing infrastructure to take advantage of the benefits of cloud computing. Cloud-based applications can be built on low-level infrastructure pieces or they can use higher-level services that provide abstraction from the management, architecting, and scaling requirements of core infrastructure.

**Hybrid:** A hybrid deployment is a way to connect infrastructure and applications between cloud-based resources and existing resources that are not located in the cloud. The most common method of hybrid deployment is between the cloud and existing on-premises infrastructure. This model enables an organization to extend and grow their infrastructure into the cloud while connecting cloud resources to internal systems.

**On-premises:** Deploying resources on-premises, using virtualization and resource management tools, is sometimes called private cloud. While on-premises deployment does not provide many of the benefits of cloud computing, it is sometimes sought for its ability to provide dedicated resources. In most cases, this deployment model is the same as legacy IT infrastructure, but it might also use application management and virtualization technologies to increase resource utilization.

**Similarities between AWS and Traditional IT**

AWS security groups, network access control lists (network ACLs), and AWS Identity and Access Management (IAM), are similar to firewalls, access control lists (ACLs), and administrators.

Elastic Load Balancing and Amazon Virtual Private Cloud (Amazon VPC) are similar to routers, network pipelines, and switches.

Amazon Machine Images (AMIs) and Amazon Elastic Compute Cloud (Amazon EC2) instances are similar to on-premises servers.

Amazon Elastic Block Store (Amazon EBS), Amazon Elastic File System (Amazon EFS), Amazon Simple Storage Service (Amazon S3), and Amazon Relational Database Service (Amazon RDS) are similar to direct attached storage (DAS), storage area networks (SAN), network attached storage (NAS), and a relational database management service (RDBMS).



































**Section 2: Advantages of Cloud Computing**

**Six Advantages of Cloud Computing**

**Trade capital expense for variable expense:** Capital expense (capex) are funds that a company uses to acquire, upgrade, and maintain physical assets. A variable expense is an expense that the person who bears the cost can easily alter or avoid. You can choose to pay only when you consume resources and pay only for the amount you consume. It also enables you to adapt to new applications with as much space as you need in minutes, instead of weeks or days. Maintenance is reduced, so you can focus more on the core goals of  your business.

**Benefit from massive economies of scale:** By using cloud computing, you can achieve a lower variable cost than you can get on your own. Because usage from hundreds of thousands of customers is aggregated in the cloud, providers such as AWS can achieve higher economies of scale, which translates into lower pay-as-you-go prices.

**Stop guessing capacity:** Eliminate guessing about your infrastructure capacity needs. When you make a capacity decision before you deploy an application, you often either have expensive idle resources or deal with limited capacity. With cloud computing, these problems go away. You can access as much or as little as you need, and scale it up and down as required with only a few minutes’ notice.

**Increase speed and agility:** In a cloud computing environment, new IT resources are only a click away, which means that you reduce the time it takes to make those resources available to your developers from weeks to just minutes. The result is a dramatic increase in agility for the organization because the cost and time that it takes to experiment and develop are significantly lower.

**Stop spending money on running and maintaining data centers:** Focus on projects that differentiate your business instead of focusing on the infrastructure. Cloud computing enables you to focus on your own customers instead of the heavy lifting of racking, stacking, and powering servers.

**Go global in minutes:** You can deploy your application in multiple AWS Regions around the world with just a few clicks. As a result, you can provide a lower latency and better experience for your customers simply and at minimal cost.






**Section 3: Introduction to Amazon Web Services (AWS)**

A **web service** is any piece of software that makes itself available over the internet and uses a **standardized format,** such as Extensible Markup Language (XML) or JavaScript Object Notation (JSON), for the request and the response of an **application programming interface (API) interaction.** It is not tied to any one operating system or programming language. It’s self-describing via an interface definition file and it is discoverable.

Amazon Web Services (AWS) is a secure cloud platform that offers a broad set of global cloud-based products. Because these products are delivered over the internet, you have on-demand access to the compute, storage, network, database, and other IT resources that you might need for your projects, and the tools to manage them. You can immediately provision and launch AWS resources. The resources are ready for you to use in minutes.

AWS offers flexibility. Your AWS environment can be reconfigured and updated on demand, scaled up or down automatically to meet usage patterns and optimize spending, or shut down temporarily or permanently. The billing for AWS services becomes an operational expense instead of a capital expense.

AWS services are designed to work together to support virtually any type of application or workload. Think of these services like building blocks, which you can assemble quickly to build sophisticated, scalable solutions, and then adjust them as your needs change.

AWS services fall under different categories, and each category contains one or more services. You can select the services that you want from these different categories to build your solutions.

**Choosing a Service**

Which service you choose to use will depend on your business goals and technology requirements.

**Amazon EC2:** You want complete control over your AWS computing resources.

**AWS Lambda:** You want to run your code and not manage or provision servers.

**AWS Elastic Beanstalk:** You want a service that deploys, manges, and scales your web applications for you.

**Amazon Lightsail:** You need a lightweight cloud platform for a simple web application.

**AWS Batch:** You need to run hundreds of thousands of batch workloads.

**AWS Outposts:** You want to run AWS infrastructure in your on-premises data center.

**Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), or AWS Fargate:** You want to implement a containers or microservices architecture.

**VMware Cloud on AWS:** You have an on-premises server virtualization platform that you want to migrate to AWS.

**Services**

**Compute Services**

Amazon EC2

AWS Lambda

AWS Elastic Beanstalk

Amazon EC2 Auto Scaling

Amazon ECS

Amazon EKS

Amazon ECR

AWS Fargate

**Security, Identity, and Compliance services**

AWS IAM

Amazon Cognito

AWS Shield

AWS Artifact

AWS KMS

**Storage Services**

Amazon S3

Amazon S3 Glacier

Amazon EFS

Amazon EBS

**Database Services**

Amazon RDS

Amazon DynamoDB

Amazon Redshift

Amazon Aurora

**Networking and Content Delivery Services**

Amazon VPC

Amazon Route 53

Amazon CloudFront

Elastic Load Balancing

**Management and Governance Services**

AWS Trusted Advisor

AWS CloudWatch

AWS CloudTrail

AWS Well-Architected Tool

AWS Auto Scaling

AWS Command Line Interface

AWS Config

AWS Management Console

AWS Organizations

**AWS Cost Management Services**

AWS Cost & Usage Report

AWS Budgets

AWS Cost Explorer

**Legend:**

•Amazon Elastic Block Store (Amazon EBS)

•Amazon Elastic Compute Cloud (Amazon EC2)

•Amazon Elastic Container Registry (Amazon ECR)

•Amazon Elastic Container Service (Amazon ECS)

•Amazon Elastic File System (Amazon EFS)

•Amazon Elastic Kubernetes Service (Amazon EKS)

•Amazon Relational Database Service (Amazon RDS)

•Amazon Simple Storage Service (Amazon S3)

•Amazon Virtual Private Cloud (Amazon VPC)

•AWS Identity and Access Management (IAM)

•AWS Key Management Service (AWS KMS)

**Three ways to interact with AWS**

**AWS Management Console:** The console provides a rich graphical interface to a majority of the features offered by AWS.

**AWS Command Line Interface (AWS CLI):** The AWS CLI provides a suite of utilities that can be launched from a command script in Linux, macOS, or Microsoft Windows.

**Software development kits (SDKs):** AWS provides packages that enable accessing AWS in a variety of popular programming languages. This makes it easy to use AWS in your existing applications and it also enables you to create applications that deploy and monitor complex systems entirely through code.


**Section 4: Moving to the AWS Cloud - The AWS Cloud Adoption Framework (AWS CAF)**

**AWS Cloud Adoption Framework (AWS CAF)**

AWS CAF provides guidance and best practices to help organizations identify gaps in skills and processes. It also helps organizations build a comprehensive approach to cloud computing, both across the organization and throughout the IT lifecycle, to accelerate successful cloud adoption.

At the highest level, th eAWS CAF organizes guidance into six areas of focus, called **perspectives.** Perspectives span people, processes, and technology. Each perspective consists of a set of **capabilities,** which covers distinct responsibilities that are owned or managed by functionally related stakeholders.

**Six Core Perspectives**

Focus on business capabilities

**Business:** Stakeholders from the Business perspective (for example, business managers, finance managers, budget owners, and strategy stakeholders) can use the AWS CAF to create a strong business case for cloud adoption and prioritize cloud adoption initiatives. Stakeholders should ensure that an organization’s business strategies and goals align with its IT strategies and goals.

**People:** Stakeholders from the People perspective (for example, human resources, staffing, and people managers) can use the AWS CAF to evaluate organizational structures and roles, new skill and process requirements, and identify gaps. Performing an analysis of needs and gaps can help prioritize training, staffing, and organizational changes to build an agile organization.** 

**Governance:** Stakeholders from the Governance perspective (for example, the Chief Information Officer or CIO, program managers, enterprise architects, business analysts, and portfolio managers) can use the AWS CAF to focus on the skills and processes that are needed to align IT strategy and goals with business strategy and goals. This focus helps the organization maximize the business value of its IT investment and minimize the business risks.

Focus on technical capabilities

**Platform:** Stakeholders from the Platform perspective (for example, Chief Technology Officer or CTO, IT managers, and solutions architects) use a variety of architectural dimensions and models to understand and communicate the nature of IT systems and their relationships. They must be able to describe the architecture of the target state environment in detail. The AWS CAF includes principles and patterns for implementing new solutions on the cloud, and for migrating on-premises workloads to the cloud.

**Security:** Stakeholders from the Security perspective (for example, Chief Information Security Officer or CISO, IT security managers, and IT security analysts) must ensure that the organization meets security objectives for visibility, auditability, control, and agility. Security perspective stakeholders can use the AWS CAF to structure the selection and implementation of security controls that meet the organization’s needs.

**Operations:** Stakeholders from the Operations perspective (for example, IT operations managers and IT support managers) define how day-to-day, quarter-to-quarter, and year-to-year business is conducted. Stakeholders from the Operations perspective align with and support the operations of the business. The AWS CAF helps these stakeholders define current operating procedures. It also helps them identify the process changes and training that are needed to implement successful cloud adoption.
























**Module 2: Cloud Economics and Billing**

**Section 1: Fundamentals of Pricing**

**AWS Pricing Model**

There are three fundamental drivers of cost with AWS: **compute, storage,** and **outbound transfer.** These characteristics vary somewhat, depending on the AWS product and pricing model you choose.

In most cases, there is no charge for inbound data transfer or for data transfer between other AWS services within the same AWS Region. There are some exceptions, so be sure to verify data transfer rates before you begin to use the AWS service.

Outbound data transfer is aggregated across services and then charged at the outbound data transfer rate. This charge appears on the monthly statement as **AWS Data Transfer Out.**

**How do you pay for AWS?**

This philosophy is what underlies AWS pricing. While the number and types of services offered by AWS have increased dramatically, our philosophy on pricing has not changed. At the end of each month, you pay for what you use. You can start or stop using a product at any time. No long-term contracts are required.

AWS offers a range of cloud computing services. For each service, you pay for exactly the amount of resources that you actually need. This utility-style pricing model includes:

Pay for what you use

Pay less when you reserve

Pay less when you use more

Pay even less as AWS grows

**Pay for what you use**

With AWS, you pay only for the services that you consume with no large upfront expenses. You can lower variable costs, so you no longer need to dedicate valuable resources to building costly infrastructure, including purchasing servers, software licenses, or leasing facilities.

Quickly adapt to changing business needs and redirect your focus on innovation and invention by paying only for what you use and for as long as you need it. All AWS services are available on demand, require no long-term contracts, and have no complex licensing dependencies.

**Pay less when you reserve**

For certain services like Amazon Elastic Compute Cloud (Amazon EC2) and Amazon Relational Database Service (Amazon RDS), you can invest in reserved capacity. With Reserved Instances, you can save up to 75 percent over equivalent on-demand capacity. Reserved Instances are available in three options:

All Upfront Reserved Instance (AURI)

Partial Upfront Reserved Instance (PURI)

No Upfront Payments Reserved Instance (NURI)

When you buy Reserved Instances, you receive a greater discount when you make a larger upfront payment. To maximize your savings, you can pay all upfront and receive the largest discount. Partial Upfront RIs offer lower discounts, but they give you the option to spend less upfront. Lastly, you can choose to spend nothing upfront and receive a smaller discount, which enables you to free capital to spend on other projects.

By using reserved capacity, your organization can minimize risks, more predictably manage budgets, and comply with policies that require longer-term commitments.

**Pay less by using more**

With AWS, you can get volume based discounts and realize important savings as your usage increases. For services like Amazon Simple Storage Service (Amazon S3), pricing is tiered, which means that you pay less per GB when you use more. In addition, **data transfer ‘in’ is always free.** Multiple storage services deliver lower storage costs based on your needs. As a result, as your AWS usage needs increase, you benefit from the economies of scale that enable you to increase adoption and keep costs under control.

As your organization evolves, AWS also gives you options to acquire services that help you address your business needs. To optimize your savings, you can choose the right combination of storage solutions that help you reduce costs while preserving performance, security, and durability.


**Pay even less as AWS grows**

AWS constantly focuses on reducing data center hardware costs, improving operational efficiencies, lowering power consumption, and generally lowering cost of doing business.

These optimizations and the substantial and growing economies of scale of AWS result in passing savings back to you as lower pricing. Since 2006, AWS has lowered pricing 75 times (as of September 2019).

Another benefit of AWS growth is that future, higher-performing resources replace current ones for no extra charge.

**Custom Pricing**

AWS realizes that every customer has different needs. If none of the AWS pricing models work for your project, custom pricing is available for high-volume projects with unique requirements.

**AWS FreeTier**

To help new AWS customers get started in the cloud, AWS offers a free usage tier (the AWS Free Tier) for new customers for up to 1 year. The AWS Free Tier applies to certain services and options. If you are a new AWS customer, you can run a free Amazon Elastic Compute Cloud (Amazon EC2) T2 micro instance for a year, while also using a free usage tier for Amazon S3, Amazon Elastic Block Store (Amazon EBS), Elastic Load Balancing, AWS data transfer, and other AWS services.

**Services with no charge**

**Amazon Virtual Private Cloud (Amazon VPC):** enables you to provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

**AWS Identity and Access Management (IAM):** controls your users’ access to AWS services and resources.

**Consolidated Billing:** a billing feature in AWS Organizations to consolidate payment for multiple AWS accounts or multiple Amazon Internet Services Private Limited (AISPL) accounts. Consolidated billing provides:

**One bill** for multiple accounts.

The ability to **easily track** each account’s charges.

The opportunity to decrease charges as a result of volume pricing discounts from **combined usage.**

You can consolidate all of your accounts using Consolidated Billing and get tiered benefits.

**AWS Elastic Beanstalk:** An even easier way for you to quickly deploy and manage applications in the AWS Cloud.

**AWS CloudFormation** gives developers and system administrators an easy way to create a collection of related AWS resources and provision them in an orderly and predictable fashion.

**Automatic Scaling** automatically adds or removes resources according to conditions you define. The resources you are using increase seamlessly during demand spikes to maintain performance and decrease automatically during demand lulls to minimize costs.

**AWS OpsWorks** is an application management service that makes it easy to deploy and operate applications of all shapes and sizes.

Though there is no charge for these services, there might be charges associated with other AWS services used with these services.

The main difference between AWS accounts and AISPL accounts is the **seller of record.** AWS accounts are administered by Amazon Web Services, Inc., but AISPL accounts are administered by Amazon Internet Services Private Limited. If you used an Indian address when you created your account, your account’s default seller of record is AISPL. By default, AISPL accounts are billed in Indian Rupees (INR).
















**Section 2: Total Cost of Ownership**

**On-premises vs Cloud**

An on-premises infrastructure is installed locally on a company’s own computers and servers. There are several fixed costs, also known as **capital expenses,** that are associated with the traditional infrastructure. Capital expenses include facilities, hardware, licenses, and maintenance staff. Scaling up can be expensive and time-consuming. Scaling down does not reduce fixed costs.

A cloud infrastructure is purchased from a service provider who builds and maintains the facilities, hardware, and maintenance staff. A customer pays for what is used. Scaling up or down is simple. Costs are easy to estimate because they depend on service use.

Using on-premises IT involves a discussion that is based on capital expenditure, long planning cycles, and multiple components to buy, build, manage, and refresh resources over time. Using the AWS Cloud involves a discussion about flexibility, agility, and consumption-based costs.

**What is Total Cost of Ownership (TCO)?**

You can identify the best option by comparing the on-premises solution to a cloud solution. Total Cost of Ownership (or TCO) is a tool that can be used for this comparison. TCO is a financial estimate that is intended to help buyers and owners determine the direct and indirect costs of a product or system. TCO includes the cost of a service, plus all the costs that are associated with owning th eservice.

In the cloud environment, TCO is used for comparing the costs of running an entire infrastructure environment for a specific workload in an on-premises or collocation facility, to the same workload running on a cloud-based infrastructure. This comparison is done for budgeting purposes or to build a business case for business decisions about the optimal deployment solution.

**TCO Considerations**

Some of the costs that are associated with data center management include:

**Server** costs for both hardware and software, and facilities costs to house the equipment.

**Storage** costs for the hardware, administration, and facilities.

**Network** costs for hardware, administration, and facilities.

**IT Labor** costs that are required to administer the entire solution.

With the cloud, most costs are upfront and readily calculated.

Calculations of in-house (on-premises) costs must take into account all:

**Direct costs** that accompany running a server, like power, floor space, storage, and IT operations to manage those resources.

**Indirect costs** of running a server, like network and storage infrastructure.

**AWS Simple Monthly Calculator**

AWS offers tools to help you with these comparisons. The **AWS Simple Monthly Calculator** helps estimate a monthly AWS bill. You can use this tool to add, modify, and remove services, and it recalculates the estimated monthly charges automatically.

The calculator incorporates a wide array of pricing calculations across all services in all Regions. It also shows a breakdown of features for each service in each Region.

The **Simple Monthly Calculator** is a tool that helps you:

Estimate monthly services costs when you use AWS.

Identify opportunities for cost reduction.

Use templates to model solutions to compare services and deployment models.

The calculator also shows common customer samples and their usage. You can choose the **Disaster Recovery and Backup** sample or **Web Application** sample and see the uses of each service.

**AWS TCO Calculator**

The **AWS TCO Calculator** helps you evaluate the Total Cost of Ownership of a solution. You can reduce the TCO by reducing your investment in large capital expenditures (capex) and using a pay-as-you-go model so you can invest in the capacity that you need when you need it.

The TCO calculator is a tool that helps you:

Estimate cost savings when using AWS.

Review a detailed set of reports, which can be used in executive presentations.

Modify assumptions that best meet your needs.

An additional benefit of the calculator includes the ability to weigh the financial considerations of owning and operating a data center versus using a cloud infrastructure. Also, the TCO Calculator explains the assumptions and the methodology behind the calculations.

**Additional Benefit Considerations**

Hard benefits include reduced spending on compute, storage, networking, and security. They also include reductions in hardware and software purchases; reductions in operational costs, backup, and disaster recovery; and a reduction in operations personnel.

**Cloud Total Cost of Ownership** defines what will be spent on the technology after adoption, or what it costs to run the collusion. Typically, a TCO analysis looks at the as-is on-premises infrastructure and compares it with the cost of the to-be infrastructure state in the cloud. While this difference might be easy to calculate, it might only provide a narrow view of the total financial impact of moving to the cloud.

A **return on investment (ROI)** analysis can be used to determine the value that is generated while considering spending and saving. This analysis starts by identifying the hard benefits in terms of direct and visible cost reductions and efficiency improvements.

Next, **soft savings** are identified. Soft savings are value points that are challenging to accurately quantify, but they can be more valuable than the hard savings. It is important for you to understand both hard and soft benefits to understand the full value of the cloud. Soft benefits include:

Reusing service and applications that enable you to define (and redefine solutions) by using the same cloud service

Increased developer productivity

Improved customer satisfaction

Agile business processes that can quickly respond to new and emerging opportunities

Increased global reach.







**Section 3: Billing**

AWS Organizations is a free account management service that enables you to consolidate multiple AWS accounts into an **organization** that you create and centrally manage. AWS Organizations includes consolidated billing and account management capabilities that help you to better meet the budgetary, security, and compliance needs of your business.

The main benefits of AWS Organizations are:

Centrally managed access policies across multiple AWS accounts.

Controlled access to AWS services.

Automated AWS account creation and management.

Consolidated billing across multiple AWS accounts.

**AWS Organizations Terminology**

An **organizational unit (OU)** is a container for accounts within a **root (basic organization).** An OU can also contain other OUs. This structure enables you to create a hierarchy that looks like an upside-down tree with the root at the top. The branches consist of child OUs and they move downward until they end in accounts, which are like the leaves of the tree.

When you attach a policy to one of the nodes in the hierarchy, it flows down and it affects all the branches and leaves.

An OU can have only one parent and, currently, each account can be a member of exactly one OU. An account is a standard AWS account that contains your AWS resources. You can attach a policy to an account to apply controls to only that one account.

**Key Features and Benefits**

AWS Organizations enables you to:

Create **service control policies (SCPs)** that centrally control AWS services across multiple AWS accounts.

Create **groups of accounts** and then attach policies to a group to ensure that the correct policies are applied across the accounts.

Simplify account management by using **application programming interfaces (APIs)** to automate the creation and management of new AWS accounts.

Simplify the billing process by setting up a single payment method for all the AWS accounts in your organization. With **consolidated billing,** you can see a combined view of charges that are incurred by all your accounts, and you can take advantage of pricing benefits from aggregated usage. Consolidated billing provides a central location to manage billing across all of your AWS accounts, and the ability to benefit from volume discounts.

**Security with AWS Organizations**

AWS Organizations does not replace associating **AWS Identity and Access Management (IAM)** policies with users, groups, and roles within an AWS account.

With IAM policies, you can allow or deny access to AWS services (such as Amazon S3), individual AWS resources (such as a specific S3 bucket), or individual API actions (such as S3:CreateBucket). An IAM policy can be applied only to IAM users, groups. or roles, and it can never restrict the AWS account root user.

In contrast, with Organizations, you use **service control policies (SCPs)** to allow or deny access to particular AWS services for individual AWS accounts or for groups of accounts in an OU. The specified actions from an attached SCP affect all IAM users, groups, and roles for an account, including the AWS account root user.

**Organizations Setup**

Keep in mind that this process assumes that you have access to two existing AWS accounts, and that you can sign in to each account as an administrator.

**Steps for setting up AWS Organizations:**

Step 1: create your organization with your current AWS account as the master account. You also invite one AWS account to join your organization and create another account as a member account.

Step 2: create two organizational units in your new organization and place the member accounts in those OUs.

Step 3: create service control policies, which enable you to apply restrictions to what actions can be delegated to users and roles in the member accounts. A service control policy is a type of organization control policy.

Step 4: test your organization's policies. Sign in as a user for each of the roles (such as OU1 or OU2) and see how the service control policies impact account access. Alternatively, you can use the IAM policy simulator to test and troubleshoot IAM and resource-based policies that are attached to IAM users, groups, or roles in your AWS account.

**Limits of AWS Organizations** 

**Limits on names**

Names must be composed of Unicode characters

Names must not exceed 250 characters in length

**Maximum and Minimum Values**

Number of AWS accounts: Varies - An invitation sent to an account counts against this limit

Number of roots: 1

Number of OUs: 1000

Number of policies: 1000

Maximum size of a service control policy document: 5120 bytes

Maximum nesting of OUs in a root: 5 levels of OUs under a root

Invitations sent per day: 20

Number of member accounts you can create concurrently: Only 5 can be in progress at one time

Number of entities to which you can attach a policy: Unlimited

**Accessing AWS Organizations**

AWS Organizations can be managed through different interfaces.

The **AWS Management Console** is a browser-based interface that you can use to manage your organization and your AWS resources. You can perform any task in your organization by using the console.

**AWS Command Line Interface (AWS CLI) tools** enable you to issue commands at your system’s command line to perform AWS Organizations tasks and AWS tasks. This method can be faster and more convenient than using the console.

You can also use **AWS software development kits (SDKs)** to handle tasks such as cryptographically signing requests, managing errors, and retrying requests automatically. AWS SDKs consist of libraries and sample code for various programming languages and platforms, such as Java, Python, Ruby, .NET, iOS, and Android.

The **AWS Organizations HTTPS Query API** gives you programmatic access to AWS Organizations and AWS. You can use the API to issue HTTPS requests directly to the service. When you use the HTTPS API, you must include code to digitally sign requests by using your credentials.

**AWS Billing and Cost Management**

**AWS Billing and Cost Management** is the service that you use to pay your AWS bill, monitor your usage, and budget your costs. Billing and Cost Management enables you to forecast and obtain a better idea of what your costs and usage might be in the future so that you can plan ahead.

You can set a custom time period and determine whether you would like to view your data at a monthly or daily level of granularity.

With the filtering and grouping functionality, you can further analyze your data using a variety of available dimensions. The **AWS Cost and Usage Report Tool** enables you to identify opportunities for optimization by understanding your cost and usage data trends and how you are using your AWS implementation.

**AWS Billing Dashboard**

The **AWS Billing Dashboard** lets you view the status of your month-to-date AWS expenditure, identify the services that account for the majority of your overall expenditure, and understand at a high level how costs are trending.

One of the graphs that is located on the dashboard is the **Spend Summary.** The Spend Summary shows you how much you spent last month, the estimated costs of your AWS usage for the month to date, and a forecast for how much you are likely to spend this month.

Another graph is **Month-to-Date Spend by Service,** which shows the top services that you use the most and the proportion of costs that are attributed to that service.

**Tools**

From the billing dashboard, you can access several other cost management tools that you can use to estimate and plan your AWS costs. These tools include AWS Bills, AWS Cost Explorer, AWS Budgets, and AWS Cost and Usage Reports.



**Monthly Bills**

The **AWS Bills page** lists the costs that you incurred over the past month for each AWS service, with a further breakdown by AWS Region and linked account.

This tool gives you access to the most up-to-date information on your costs and usage, including your monthly bill and the detailed breakdown of the AWS services that you use.

**Cost Explorer**

The **AWS Billing and Cost Management** console includes the **Cost Explorer page** for viewing your AWS cost data as a graph.

With Cost Explorer, you can visualize, understand, and manage your AWS costs and usage over time.

The Cost Explorer includes a default report that visualizes your costs and usage for your top cost-incurring AWS services. The monthly running costs report gives you an overview of all your costs for the past 3 months. It also provides forecasted numbers for the coming month, with a corresponding confidence interval.

The Cost Explorer is a free tool that enables you to:

View charts of your costs

View cost data for the past 13 months

Forecast how much you are likely to spend over the next 3 months

Discover patterns in how much you spend on AWS resources over time and identify cost problem areas.

Identify the services that you use the most

View metrics, like which Availability Zones have the most traffic or which linked AWS account is used the most.

**Forecast and Track Costs**

**AWS Budgets** uses the cost visualization that is provided by Cost Explorer to show you the status of your budgets and to provide forecasts of your estimated costs.

You can also use AWS Budgets to create notifications for when you go over your budget for the month, or when your estimated costs exceed your budget. Budgets can be tracked at the monthly, quarterly, or yearly level, and you can customize the start and end dates. Budget alerts can be sent via email or via **Amazon Simple Notification Service (Amazon SNS).**

**Cost and Usage Reporting**

The **AWS Cost and Usage Report** is a single location for accessing comprehensive information about your AWS costs and usage. This tool lists the usage for each service category that is used by an account (and its users) in hourly or daily line items, and any tax that you activated for tax allocation purposes.

You can choose to have AWS to publish billing reports to an S3 bucket. These reports can be updated once a day.




























**Section 4: Technical Support**

**AWS Support**

AWS Support can provide you with a unique combination of tools and expertise based on your current or future planned use cases.

AWS Support

AWS Support Plan

AWS Support was developed to provide complete support and the right resources to aid your success. AWS Support can vary the type of support that is provided, depending on the customer’s needs and goals.

Experimenting with AWS

Production use of AWS

Business-critical use of AWS

With AWS, customers can plan, deploy, and optimize with confidence.

If you would like proactive guidance, AWS Support has **Technical Account Managers (TAMs)** who are designated as that user’s primary point of contact. The TAM can provide guidance, architectural review, and continuous ongoing communication to keep you informed and prepared as you plan, deploy, and optimize your solutions.

If you want to ensure that you follow best practices to increase performance and fault tolerance in the AWS environment, AWS Support has **AWS Trusted Advisor.** AWS Trusted Advisor is like a customized cloud expert. It is an online resource that checks for opportunities to reduce monthly expenditures and increase productivity.

For account assistance, the **Support Concierge** is a billing and account expert who will provide quick and efficient analysis on billing and account issues. The concierge addresses all non-technical billing and account-level inquiries.

**Support Plans**

AWS Support offers four support plans:

**Basic Support Plan**

24/7 access to customer service, documentation, whitepapers and support forums.

Access to six core Trusted Advisor checks.

Access to Personal Health Dashboard

The **Development Support Plan** offers resources for customers that are testing or doing early development on AWS, and any customers who:

Want access to guidance and technical support.

Are exploring how to quickly put AWS to work.

Use AWS for non-production workloads or applications.

The **Business Support Plan** offers resources for customers that are running production workloads on AWS, and any customers who:

Run one or more applications in production environments.

Have multiple services activated, or use key services extensively.

Depend on their business solutions to be available, scalable, and secure.

The **Enterprise Support Plan** offers resources for customers that are running business and mission-critical workloads on AWS, and any customers who want to:

Focus on proactive management to increase efficiency and availability.

Build and operate workloads that follow AWS best practices.

Use AWS expertise to support launches and migrations.

Use a Technical Account Manager (TAM), who provides technical expertise for the full range of AWS services and obtains a detailed understanding of your use case and technology architecture. The TAM is the primary point of contact for ongoing support needs.

**Case Severity and Response Times**

In addition to understanding the costs that are associated with different support plans, it is critical to understand the service levels that are associated with each plan.

There are five different severity levels:

**Critical** – Your business is at risk. Critical functions of your application are unavailable.

Response: 15 min or less

**Urgent** – Your business is significantly impacted. Important functions of your application are unavailable.

Response: 1 hour or less

**High** – Important functions of your application are impaired or degraded.

Response: 4 hours or less

**Normal** – Non-critical functions of your application are behaving abnormally, or you have a time-sensitive development question.

Response: 12 hours or less

**Low** – You have a general development question, or you want to request a feature.

Response: 24 hours or less


Plan Severity Coverage:

Basic Plan: No case support

Developer Plan (Business hours): Normal and Low

Business Plan (24/7): Urgent, High, Normal, Low

Enterprise Plan (24/7): Critical, Urgent, High, Normal, Low



































**Module 3: AWS Global Infrastructure Overview**

**Section 1: AWS Global Infrastructure**

**AWS Global Infrastructure**

The **AWS Global Infrastructure** is designed and built to deliver a flexible, reliable, scalable, and secure cloud computing environment with high-quality global network performance.

**AWS Regions**

The AWS Cloud Infrastructure is built around Regions. AWS has 22 Regions worldwide. An **AWS Region** is a physical geographical location with one or more **Availability Zones.** Availability Zones in turn consist of one or more **data centers.**

To achieve fault tolerance and stability, Regions are isolated from one another. Resources in one Region are not automatically replicated to other Regions. When you store data in a specific Region, it is not replicated outside that Region.

It is your responsibility to replicate data across Regions, if your business needs require it.

AWS REgions that were introduced before March 20, 2019 are enabled by default. Regions that were introduced after March 20, 2019, such as Asia Pacific (Hong Kong) and Middle East (Bahrain), are disabled by default. You must enable these Regions before you can use them.You can use the AWS Management Console to enable or disable a Region.

Some Regions have restricted access. An Amazon AWS (China) account provides access to the Beijing and Ningxia Regions only. The isolated **AWS GovCloud (US)** Region is designed to allow US government agencies and customers to move sensitive workloads into the cloud by addressing their specific regulatory and compliance requirements.

**Selecting a Region**

One essential consideration is **data governance and legal requirements.** Local laws might require that certain information be kept within geographical boundaries. Such laws might restrict the Regions where you can offer content or services.

All else being equal, it is generally desirable to run your applications and store your data in a Region that is as close as possible to the user and systems that will access them. This will help you **reduce latency.** CloudPing is one website that you can use to test latency between your location and all AWS Regions.

Not all services are available in all Regions.

There is some variation in the cost of running services, which can depend on which Region you choose.

**Availability Zones**

Each AWS Region has multiple, isolated locations that are known as **Availability Zones.**

Each AZ provides the ability to operate applications and databases that are more highly available, fault-tolerant, and scalable than would be possible with a single data center. Each AZ can include multiple data centers (typically three), and at full-scale, they can include hundreds of thousands of servers. They are fully isolated partitions of the AWS Global Infrastructure. AZs have their own power infrastructure, and they are physically separated by many kilometers from other AZs, though all AZs are within 100 km of each other.

All AZs are interconnected with high-bandwidth, low-latency networking over fully redundant, dedicated fiber that provides high-throughput between AZs. The network accomplishes synchronous replication between AZs.

AZs help build highly available applications. When an application is partitioned across AZs, companies are better isolated and protected from issues such as lightning, tornadoes, earthquakes, and more.

You are responsible for selecting the AZs where your systems will reside. Systems can span multiple AZs. AWS recommends replicating across AZs for resiliency. You should design your systems to survive the temporary or prolonged failure of an AZ if a disaster occurs.





**AWS Data Centers**

The foundation for the AWS infrastructure is the data centers. Customers do not specify a data center for the deployment of resources. Instead, an AZ is the most granular level of specification that a customer cna make. However, a data center is the location where the actual data resides. Amazon operates state-of-the-art, highly available data centers. Although rare, failures can occur that affect the availability of instances in the same location. If you host all your instances in a single location that is affected by such a failure, none of your instances will be available.

Data centers are securely designed with several factors in mind:

Each location is carefully evaluated to **mitigate environmental risk.**

Data centers have a **redundant design** that anticipates and tolerates failure while maintaining service levels.

To ensure availability, **critical system components are backed up** across multiple AZs.

To ensure capacity, AWS continuously monitors service usage to deploy infrastructure to support availability commitments and requirements.

Data center **locations are not disclosed** and all access to them is restricted.

In case of failure, automated processes move data traffic away from the affected area.

AWS uses **custom network equipment** sourced from **multiple original device manufacturers (ODMs).** ODMs design and manufacture products based on specifications from a second company. The second company then rebrands the products for sale.

**Points of Presence**

**Amazon CloudFront** is **a content delivery network (CDN)** used to distribute content to end users to reduce latency. **Amazon Route 53** is a DNS service. Requests going to either one of these services will be routed to the nearest **edge location** automatically in order to lower latency.

AWS **Points of Presence** are located in most of the major cities (69 cities in total) across 30 countries around the world. By **continuously measuring internet connectivity, performance and computing to find the best way to route requests,** the Points of Presence deliver a better near real-time user experience. They are used by many AWS services, including Amazon CloudFront, Amazon Route 53, AWS Shield, and AWS Web Application Firewall (AWS WAF) services.

**Regional edge caches** are used by default with Amazon CloudFront. Regional edge caches are used when you have content that is not accessed frequently enough to remain in an **edge location.** Regional edge caches absorb this content and provide an alternative to that content having to be fetched from the origin server.

**AWS Infrastructure Features**

Benefits of AWS Global Infrastructure:

**Elastic and Scalable.** This means resources can dynamically adjust to increase or decrease in capacity requirements. It can also rapidly adjust to accommodate growth.

**Fault Tolerant.** This means it has a built-in component redundancy which enables it to continue operations despite a failed component.

Requires minimal to no human intervention, while providing **high availability** with minimal downtime.

**Section 2: AWS Services and Service Category**

**AWS Foundational Services**

Compute

Networking

Storage

**Storage Service Category**

**Amazon Simple Storage Service (Amazon S3):** an object storage service that offers scalability, data availability, security, and performance. Use it to store and protect any amount of data for websites, mobile apps, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

**Amazon Elastic Block Store (Amazon EBS):** a high-performance block storage that is designed for use with Amazon EC2 for both throughput and transaction intensive workloads. It is used for a broad range of workloads, such as relational and non-relational databases, enterprise applications, containerized applications, big data analytics engines, files systems, and media workflows.

**Amazon Elastic File System (Amazon EFS):** provides a scalable, fully managed elastic Network File System (NFS) file system for use with AWS Cloud services and on-premises resources. It is built to scale on demand to petabytes, growing and shrinking automatically as you add and remove files. It reduces the need to provision and manage capacity to accommodate growth.

**Amazon Simple Storage Service Glacier**: a secure, durable, and extremely low-cost Amazon S3 cloud storage class for data archiving and long-term backup. It is designed to deliver 11 9s of durability, and to provide comprehensive security and compliance capabilities to meet stringent regulatory requirements.

**Compute Service Category**

**Amazon Elastic Compute Cloud (Amazon EC2)** provides resizable compute capacity as virtual machines in the cloud.

**Amazon EC2 Auto scaling** enables you to automatically add or remove EC2 instances according to conditions that you define.

**Amazon Elastic Container Service (Amazon ECS)** is a highly scalable, high-performance container orchestration service that supports Docker containers.

**Amazon Elastic Container Registry (Amazon ECR)** is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images.

**AWS Elastic Beanstalk** is a service for deploying and scaling web applications and services on familiar servers such as Apache and Microsoft Internet Information Services (IIS).

**AWS Lambda** enables you to run code without provisioning or managing servers. You pay only for the compute time that you consume. There is no charge when your code is not running.

**Amazon Elastic Kubernetes Service (Amazon EKS)** makes it easy to deploy, manage, and scale containerized applications that use Kubernetes on AWS.

**AWS Fargate** is a compute engine for Amazon ECS that allows you to run containers without having to manage servers or clusters.

**Database Service Category**

**Amazon Relational Database Service (Amazon RDS)** makes it easy to set up, operate, and scale a relational database in the cloud. It provides resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching, and backups.

**Amazon Aurora** is a MySQL and PostgreSQL-compatible relational database. It is up to five times faster than standard MySQL databases and three times faster than standard PostgreSQL databases.

**Amazon Redshift** enables you to run analytic queries against petabytes of data that is stored locally in Amazon Redshift, and directly against exabytes of data that are stored in Amazon S3. It delivers fast performance at any scale.

**Amazon DynamoDB** is a key-value and document database that delivers single-digit millisecond performance at any scale, with built-in security, backup and restore, and in-memory caching.

**Networking and Content Delivery Service Category**

**Amazon Virtual Private Cloud (Amazon VPC)** enables you to provision logically isolated sections of the AWS Cloud.

**Elastic Load Balancing** automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions.

**Amazon CloudFront** is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and application programming interfaces (APIs) to customers globally , with low latency and high transfer speeds.

**AWS Transit Gateway** is a service that enables customers to connect their Amazon Virtual Private Cloud (VPCs) and their on-premises networks to a single gateway.

**Amazon Route 53** is a scalable DNS web service designed to give you a reliable way to route end users to internet applications.

**AWS Direct Connect** provides a way to establish a dedicated private network connection from your data center or office to AWS, which can reduce network costs and increase bandwidth throughput.

**AWS VPN** provides a secure private tunnel from your network or device to the AWS global network.

**Security, Identity, and Compliance Service Category**

**AWS Identity and Access Management (IAM)** enables you to manage access to AWS services and resources securely. By using IAM, you can create and manage AWS users and groups. You can use IAM permissions to allow and deny user and group access to AWS resources.

**AWS Organizations** allows you to restrict what services and actions are allowed in your accounts.

**Amazon Cognito** lets you add user sign-up, sign-in, and access control to your web and mobile apps.

**AWS Artifact** provides on-demand access to AWS security and compliance reports and select online agreements.

**AWS Key Management Service (AWS KMS)** enables you to create and manage keys. You can use AWS KMS to control the use of encryption across a wide range of AWS services and in your applications.

**AWS Shield** is a managed DDoS protection service that safeguards applications running on AWS.



**AWS Cost Management Service Category**

**The AWS Cost and Usage Report** contains the most comprehensive set of AWS cost and usage data available, including additional metadata about AWS services, pricing, and reservations.

**AWS Budgets** enables you to set custom budgets that alert you when your costs or usage exceed (or are forecasted to exceed) your budgeted amount.

**AWS Cost Explorer** has an easy-to-use interface that enables you to visualize, understand, and manage your AWS costs and usage over time.

**Management and Governance Service Category**

**The AWS Management Console** provides a web-based user interface for accessing your AWS account.

**AWS Config** provides a service that helps you track resource inventory and changes.

**Amazon CloudWatch** allows you to monitor resources and applications.

**AWS Auto Scaling** provides features that allow you to scale multiple resources to meet demand.

**AWS Command Line Interface** provides a unified tool to manage AWS services.

**AWS Trusted Advisor** helps you optimize performance and security.

**AWS Well-Architected Tool** provides help in reviewing and improving your workloads.

**AWS CloudTrail** tracks user activity and API usage.


















**Module 4: AWS Cloud Security**

**Section 1: AWS Shared Responsibility Model**

Security and compliance are a shared responsibility between AWS and the customer. The differentiation of who is responsible for what is commonly referred to as **security of the cloud versus security “in” the cloud.**

**AWS** operates, manages, and controls the components from the software virtualization layer down to the physical security of the facilities where AWS services operate. **AWS is responsible** for protecting the infrastructure that runs all the services that are offered in the AWS Cloud. This infrastructure is composed of the hardware, software, networking, and facilities that run the AWS Cloud services.

**The customer is responsible** for the encryption of data at rest and data in transit. The customer should also ensure that the network is configured for security and that security credentials and logins are managed safely. Additionally, the customer is responsible for the configuration of security groups and the configuration of the operating system that run on compute instances that they launch (including updates and security patches).

**AWS Responsibility: Security of the Cloud**

AWS is responsible for the security of the cloud.

Under the AWS shared responsibility model, AWS operates, manages, and controls the components from the bare metal host operating system and hypervisor virtualization layer down to the physical security of the facilities where the services operate. It means that AWS is responsible for protecting the global infrastructure that runs all the services that are offered in the AWS Cloud. The global infrastructure includes AWS Regions, Availability Zones, and edge locations.

AWS is responsible for the physical infrastructure that hosts your resources, including:

**Physical security of data centers** with controlled, need-based access; located in nondescript facilities, with 24/7 security guards; two-factor authentication; access logging and review; video surveillance; and disk degaussing and destruction.

**Hardware infrastructure,** such as servers, storage devices, and other appliances that AWS relies on.

**Software infrastructure,** which hosts operating systems, service applications, and virtualization software.

**Network infrastructure,** such as routers, switches, load balancers, firewalls, and cabling. AWS also continuously monitors the network at external boundaries, secures access points, and provides redundant infrastructure with intrusion detection.

**Customer Responsibility: Security in the Cloud**

The **customer is responsible** for what is implemented by using AWS services and for the applications that are connected to AWS. The security steps that you must take depend on the services that you use and the complexity of your system.

Customer responsibilities include selecting and securing any instance operating systems, securing the applications that are launched on AWS resources, security group configurations, firewall configurations, network configurations, and secure account management.

When customers use AWS services, they maintain complete control over their content. Customers are responsible for managing critical content security requirements, including:

What content they choose to store on AWS

Which AWS services are used with the content

In what country that content is stored

The format and structure of that content and whether it is masked, anonymized, or encrypted

Who has access to that content and how those access rights are granted, managed, and revoked

Customers retain control of what security they choose to implement to protect their own data, environment, applications, IAM configurations, and operating systems.

**Service Characteristics and Security Responsibility**

**Infrastructure as a service (IaaS)** refers to services that provide basic building blocks for cloud IT, typically including access to configure networking, computers (virtual or on dedicated hardware), and data storage space. Cloud services that can be characterized as IaaS **provide the customer with the highest level of flexibility and management control** over IT resources. IaaS services are most similar to existing on-premises computing resources that many IT departments are familiar with today.

AWS services, such as **Amazon EC2,**  can be categorized as **IaaS** and thus **requires the customer to perform all necessary security configuration and management tasks.** Customers who deploy EC2 instances are responsible for managing the guest operating system (including updates and security patches), any application software that is installed on the instances, and the configuration of the security groups that were provided by AWS.

**Platform as a Service (PaaS)** refers to services that remove the need for the customer to manage the underlying infrastructure. PaaS services enable the customer to focus entirely on deploying and managing applications. Customers don’t need to worry about resource procurement, capacity planning, software maintenance, or patching.

AWS services such as **AWS Lambda** and **Amazon RDS** can be categorized as **PaaS** because **AWS operates the infrastructure layer, the operating system, and platforms.** Customers only need to access the endpoints to store and retrieve data. With PaaS services, customers are responsible for managing their data, classifying their assets, and applying the appropriate permissions. However, these services act more like managed services, with AWS handling a larger portion of the security requirements. For these services, AWS handles basic security tasks, such as operating system and database patching, firewall configuration, and disaster recovery.

**Software as a Service (SaaS)** refers to services that provide centrally hosted software that is typically accessible via a web browser, mobile app, or application programming interface (API). The licensing model for SaaS offerings is typically subscription or pay as you go. With SaaS offerings, customers do not need to manage the infrastructure that supports the service. Some AWS services, such as **AWS Trusted Advisor, AWS Shield,** and **Amazon Chime,** could be categorized as SaaS offerings, given their characteristics.

**AWS Trusted Advisor** is an online tool that analyzes your AWS environment and provides real-time guidance and recommendations to help provision real-time guidance and recommendations to help you provision your resources by following AWS best practices. The Trusted Advisor service is offered as part of your AWS Support plan. Some of the Trusted Advisor features are free to all accounts, but Business Support and Enterprise Support customers have access to the full set of Trusted Advisor checks and recommendations.

**AWS Shield** is a managed distributed denial of service (DDoS) protection service that safeguards applications running on AWS. It provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection. AWS Shield Advanced is available to all customers. However, to contact the DDoS Response Team, customers must have either Enterprise Support or Business Support from AWS Support.

**Amazon Chime** is a communications service that enables you to meet, chat, and place business calls inside and outside your organization, all using a single application. It is a pay-as-you-go communications service with no upfront fees, commitments, or long-term contracts.

**Section 2: AWS Identity and Access Management (IAM)**

**AWS Identity and Access Management (IAM)**

**AWS Identity and Access Management (IAM)** allows you to control access to compute, storage, database, and application services in the AWS Cloud. IAM can be used to handle authentication, and to specify and enforce authorization policies so that you can specify which users can access which services.

IAM is a tool that centrally manages access to launching, configuring, managing, and terminating resources in your AWS account. It provides granular control over access to resources, including the ability to specify exactly which **API** calls the user is authorized to make to each service. Whether you use the AWS Management Console, the AWS CLI, or the AWS software development kits (SDKs), every call to an AWS service is an API call.

With IAM, you can manage which resources can be accessed by who, and how these resources can be accessed. You can grant different permissions to different people for different resources. 

IAM is a feature of your AWS account, and it is offered at no additional charge.

**IAM Essential Components**

An **IAM user** is a person or application that is defined in an AWS account, and that must make API calls to AWS products. Each user must have a unique name (with no spaces in the name) within the AWS account, and a set of security credentials that is not shared with other users. These credentials are different from the AWS account root user security credentials. Each user is defined in one and only one AWS account.


An **IAM group** is a collection of IAM users. You can use IAM groups to simplify specifying and managing permissions for multiple users.

An **IAM policy** is a document that defines permissions to determine what users can do in the AWS account. A policy typically grants access to specific resources and specifies what the user can do with those resources. Policies can also explicitly deny access.

An **IAM role** is a tool for granting temporary access to specific AWS resources in an AWS account.

**Authentication** is a basic computer security concept: a user or system must first prve their identity. When you define an IAM user, you select what type of access the user is permitted to use to access AWS resources. You can assign two different types of access to users: programmatic access and AWS Management Console access. You can assign programmatic access only, console access only, or you can assign both types of access.

If you grant **programmatic access,** the IAM user will be required to present an **access key ID** and a **secret access key** when they make an AWS API call by using the AWS CLI, the AWS SDK, or some other development.

If you grant **AWS Management Console access,** the IAM user will be required to fill in the fields that appear in the browser login window. The user is prompted to provide either the 12-digit account ID or the corresponding account alias. The user must also enter their IAM user name and password. If **multi-factor authentication (MFA)** is enabled for the user, they will also be prompted for an authentication code.

**IAM MFA**

AWS services and resources can be accessed by using the AWS Management Console, the AWS CLI, or through SDKs and APIs. For increased security, we recommend enabling MFA.

With MFA, users and systems must provide an **MFA token,** in addition to the regular sign-in credentials, before they can access AWS services and resources.

Options for generating the MFA authentication token include **virtual MFA-compliant applications** (such as Google Authenticator or Authy 2-Factor Authentication), **U2F security key devices,** and **hardware MFA devices.**

**Authorization: What actions are permitted**

**Authorization** is the process of determining what permissions a user, service or application should be granted. After a user has been authenticated, they must be authorized to access AWS services.

By default, IAM users do not have permissions to access any resources or data in an AWS account. Instead, you must explicitly grant permissions to a user, group, or role by creating a **policy**, which is a document in JavaScript Object Notation (JS A policy lists permissions that allow or deny access to resources in (JSON) format. A policy lists permissions that allow or deny access to resources in the AWS account.

**IAM Authorization**

To assign permission to a user, group or role, you must create an **IAM policy** (or find an existing policy in the account). There are no default permissions. All actions in the account are denied to the user by default (implicit deny) unless those actions are explicitly allowed. Any actions that you do not explicitly allow are denied. Any actions that you explicitly deny are always denied.

The **principle of least privilege** is an important concept in computer security. It promotes that you grant only the minimal user privileges needed to the user, based on the needs of your users. When you create IAM policies, it is a best practice to follow this security advice of granting least privilege. Determine what users need to be able to do and then craft policies for them that let the users perform only those tasks. 

The scope of the IAM service configurations is **global.** The settings are not defined at an AWS Region level. IAM settings apply across all AWS Regions.

**IAM Policies**

An IAM policy is a formal statement of permissions that will be granted to an entity. Policies can be attached to any IAM entity. Entities include users, groups, roles, or resources. Policies specify what actions are allowed, which resources to allow the actions on, and what the effect will be when the user requests access to the resources.

There are two types of IAM policies. **Identity-based policies** are permissions policies that you can attach to a principal (or identity) such as an IAM user, role, or group. These policies control what actions that identity can perform, on which resources, and under what conditions. Identity-based policies can be further categorized as:

**Managed policies:** Standalone identity-based policies that you can attach to multiple users, groups, and roles in your AWS account.

**Inline policies:** Policies that you create and manage, and that are embedded directly into a single user group or role.

**Resource-based policies** are JSON policy documents that you attach to a resource, such as an S3 bucket. These policies control what actions a specified principal can perform on that resource, and under what conditions.

**Resource-based Policies**

While identity-based policies are attached to a user, group, or role, **resource-based policies** are attached to a resource, such as an S3 bucket. These policies specify who can access the resource and what actions they can perform on it.

Resource-based policies are defined **inline only,** which means that you define the policy on the resource on the resource itself, instead of creating a separate IAM policy document that you attach.

**IAM Permissions**

IAM policies enable you to fine-tune privileges that are granted to IAM users, groups, and roles.

When IAM determines whether a permission is allowed, IAM first checks for the existence of any applicable **explicit denial policy.** If no explicit denial exists, it then checks for any applicable **explicit allow policy.** If neither an explicit deny nor an explicit allow policy exists, IAM reverts to the default, which is to deny access. This process is referred to as an **implicit deny.** The user will be permitted to take the action only if the requested action is not explicitly denied and is explicitly allowed.

**IAM Groups**

An **IAM group** is a collection of IAM users. IAM groups offer a convenient way to specify permissions for a collection of users, which can make it easier to manage the permissions for those users.

Important characteristics of IAM groups:

A group can contain many users, and a user can belong to multiple groups.

Groups cannot be nested. A group can contain only users, and a group cannot contain other groups.

There is no default group that automatically includes all users in the AWS account. If you want to have a group with all account users in it, you need to create the group and add each new user to it.

**IAM Roles**

An **IAM** **role** is an IAM identity you can create in your account that has specific permissions. An IAM role is **similar to an IAM user** because it is also an AWS identity that you can attach permissions policies to, and those permissions determine what the identity can and cannot do in AWS. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it. Instead, when you assume a role, the role provides you with temporary security credentials for your role session.

You can **use roles to delegate access to users, applications, or services** that do not normally have access to your AWS resources. 

**Section 3: Securing a new AWS account**

**AWS account root user access versus IAM access**

When you first create an AWS account, you begin with a single sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the **AWS account root user** and it is accessed by signing into the AWS Management Console with the email address and password that you used to create the account. AWS account root users have (and retain) **full access** to all resources in the account. Therefore, AWS strongly recommends that you do not use account root user credentials for day-to-day interactions with the account.

Instead, AWS recommends that you use IAM to create additional users and assign permissions to these users, following the principle of least privilege.

**Securing a new AWS account: Account root user**

To stop using the account root user, take the following steps:

While you are logged into the account root user, create an IAM user for yourself with AWS Management Console access enabled (but do not attach any permissions to the user yet). Save the IAM user access keys if needed.

Next, create an IAM group, give it a name (such as FullAccess), and attach IAM policies to the group that grant full access to at least a few of the services you will use. Next, add the IAM user to the group

Disable and remove your account root user access keys, if they exist.

Enable a password policy for all users. Copy the **IAM users sign-in link** from the IAM Dashboard page. Then, sign out as the account root user.

Browse to the IAM users sign-in link that you copied, and sign into the account by using your new IAM user credentials.

Store your account root user credentials in a secure place.

**Securing a new AWS account: MFA**

Another recommended step for securing a new AWS account is to require multi-factor authentication (MFA) for the account root user login and for all other IAM user logins. You can also use MFA to control programmatic access.

You have a few options for retrieving the MFA token that is needed to log in when MFA is enabled. Options include virtual MFA-compliant applications (such as Google Authenticator and Authy Authenticator), U2F security key devices, and hardware MFA options that provide a key fob or display card.

**Securing a new AWS account: AWS CloudTrail**

AWS CloudTrail is a service that logs all API requests to resources in your account. In this way, it enables operational auditing on your account.

AWS CloudTrail is enabled on account creation by default on all AWS accounts, and it keeps a record of the last 90 days of account management event activity. You can view and download the last 90 days of your account activity for *create*, *modify*, and *delete* operations of[ ](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html)[services that are supported by CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html) without needing to manually create another trail. 

To enable CloudTrail log retention beyond the last 90 days and to enable alerting whenever specified events occur, create a new trail (which is described at a high level on the slide).




**Securing a new AWS account: Billing reports**

An additional recommended step for securing a new AWS account is to enable billing reports, such as the **AWS Cost and Usage Report**. Billing reports provide information about your use of AWS resources and estimated costs for that use. AWS delivers the reports to an Amazon S3 bucket that you specify and AWS updates the reports at least once per day.

The AWS Cost and Usage Report tracks usage in the AWS account and provides estimated charges, either by the hour or by the day.

**Activate MFA on the account root user**

Before you create IAM users in the account, activate MFA on the account root user. To log in as the account root user, use the email address that you used to create the account. The account root user has access to everything, which is why it is important to secure this account with restrictions.

To configure MFA:

1\.Click the **Activate MFA on your root account** link.

2\.Click **Manage MFA**.

3\.Click **Assign MFA device**. You have three options: **Virtual MFA device**, **U2F security key**, and **Other hardware MFA device**. A hardware device is an actual hardware device.

4\.For purposes of this demonstration, select **Virtual** **MFA device** and then click **Continue**.

5\.A new dialog box appears and asks you to configure a virtual MFA device. An app (such as Google Authenticator) must be downloaded for this task. After the download is complete, click **Show QR code**. 

6\.In the authenticator application, choose the **plus** **sign (+)**.

7\.Scan the barcode, and enter the first authentication code.

8\.Wait a moment for the second code to display, and enter the second code.

9\.Click the **Assign MFA** button.

10\. Click **Finish** and refresh your browser.

In the **Security Status** panel, it should now show a green checkmark icon, which indicates that MFA is now activated on the account root user.






**Create an individual IAM user**

Most AWS accounts are shared by multiple users in an organization. To support this practice, you can set up each user with individually assigned permissions, or you can add users to the appropriate IAM group that grants them specific permissions.

An AWS best practice is to provide each user with their own IAM user login so that they do not log in as the account root user with global privileges, or use the same credentials as someone else to log in to the account.

To configure this setup:

1\. Click **Create individual IAM users** and then select **Manage Users**.

2\.Select **Add user** and specify a new user name. Note that user names cannot have spaces.

3\.Select the **Access type**. There are two access types (you can grant either type or both types to the user, but for the purposes of this demonstration, grant both types):

•**Programmatic access** enables the user to have AWS CLI access to provision resources. This option will generate an access key one time. This access key must be saved because it will be used for all future access.

•**AWS Management Console access** enables the user to log in to the console.

4\.If you chose to grant console access, either choose **Autogenerate password**,** or select **Custom password** and enter one.

5\.Click **Next: Permissions**.

Next, you will assign permissions. You have three options for assigning permissions:

•Add user to group

•Copy permissions from an existing user

•Attach existing policies directly

•

6\.You want to add the user to a group, so select **Add user to group** and then choose **Create group**.

Note: A group is where you put users to inherit the policies that are assigned to the group.

7\.Give the group a name. In this example, give the lead developer administrative access and then choose **Create group**.

8\.Select **Next Review** to review what will be created, and then choose **Create user**.

When a user is created—and assuming you enabled both programmatic and console access when you defined the **Access type** setting and created the user—several artifacts will be generated:

1\.An **access key ID** that can be used to sign AWS API calls when the user uses the AWS CLI or AWS SDKs.

2\.A **secret access key** that is also used to sign AWS API calls when the user uses the AWS CLI or AWS SDKs.

3\.A **password** that can be used to log in to the AWS Management Console.

Choose **Show** to display the values in each field. The credentials can also be downloaded by choosing **Download .csv**. This time is the only time when you have the option to download these credentials. You will not have an opportunity to retrieve the secret access key after this screen. Thus, you should either download the credentials, or—at the minimum—copy the secret access key, and paste it in a safe location.

**Important:** Never store these credentials in a public place (for example, never embed these credentials in code that you upload to GitHub or elsewhere). This information can be used to access your account. If you ever have a concern that your credentials have been compromised, log in as a user with IAM administrator access permissions and delete the existing access key. You can then optionally create a new access key.

When you return to the IAM Dashboard, the **Create individual IAM users** and **Use groups to assign permissions** security status items should show that they were addressed.

The remaining security item to address is to apply an IAM password policy.

The IAM password policy is a set of rules that defines the type of password that an IAM user can set.

Select the rules that the passwords should comply with and then choose **Apply password policy**.

**Section 4: Securing Accounts**

**AWS Organizations**

**AWS Organizations** is an account management service that enables you to consolidate multiple AWS accounts into an *organization* that you create and centrally manage. Here, the focus is on the security features that AWS Organizations provides.

One helpful security feature is that you can **group accounts into organizational units** (OUs) and attach different access policies to each OU. 

Another security feature is that **AWS Organizations integrates with and supports IAM.** AWS Organizations expands that control to the account level by giving you control over what users and roles in an account or group of accounts can do. The resulting permissions are the logical intersection of what is allowed by the AWS Organizations policy settings and what permissions are explicitly granted by IAM in the account for that user or role. The user can access only what is allowed by **both** th eAWS Organizations policies and IAM policies.

Finally, AWS Organizations **provides service control policies (SCPs)** that enable you to specify the maximum permissions that member accounts in the organization can have. In SCPs, you can restrict which AWS services, resources, and individual actions the users and roles in each member account can access. **These restrictions even override the administrators of member accounts.** When AWS Organizations blocks access to a service, resource, or API action, a user or role in that account can’t access it, even if an administrator of a member account explicitly grants such permissions.

**AWS Organizations: Service control policies**

SCPs offer central control over the **maximum available permissions** for all accounts in your organization, enabling you to ensure that your accounts stay in your organization’s access control guidelines. SCPs are available only in an organization that has all features enabled, including consolidated billing. SCPs aren’t available if your organization has enabled only the consolidated billing features.

**SCPs are similar to IAM permission policies** and they use almost the same syntax. However, an SCP never grants permissions. Instead, SCPs are JSON policies that specify the maximum permissions for an organization or OU. Attach an SCP to the organization root or an OU defines a safeguard for the actions that accounts in the organization root or OU can do. However, it is not a substitute for well-managed IAM configurations within each account. You must still attach IAM policies to users an droles in your organization’s accounts to actually grant permissions to them.

**AWS Key Management Service (AWS KMS)**

**AWS Key Management Service (AWS KMS)** is a service that enables you to create and manage encryption keys, and to control the use of encryption across a wide range of AWS services and your applications. AWS KMS is a secure and resilient service that uses hardware security modules (HSMs) that were validated under **Federal Information Processing Standards (FIPS) 140-2** (or are in the process of being validated) to protect your keys. AWS KMS also integrates with AWS CloudTrail to provide you with logs of all key usage to help meet your regulatory and compliance needs.

**Customer master keys (CMKs)** are used to control access to data encryption keys that encrypt and decrypt your data. You can create new master keys when you want, and you can manage who has access to these keys and which services they can be used with. You can also import keys from your own key management infrastructure into AWS KMS.

AWS KMS integrates with most AWS services, which means that you can use AWS KMS master keys to control the encryption of the data that you store in these services.

**Amazon Cognito**

Amazon Cognito provides solutions to control access to AWS resources from your application. You can define roles and map users to different roles so your application can access only the resources that are authorized for each user.

Amazon Cognito uses common identity management standards, such as **Security Assertion Markup Language (SAML) 2.0**. SAML** is an open standard for exchanging identity and security information with applications and service providers. Applications and service providers that support SAML enable you to sign in by using your corporate directory credentials, such as your user name and password from Microsoft Active Directory. With SAML, you can use single sign-on (SSO) to sign in to all of your SAML-enabled applications by using a single set of credentials.

Amazon Cognito helps you **meet multiple security and compliance requirements**, including requirements for highly regulated organizations such as healthcare companies and merchants. Amazon Cognito is eligible for use with the US Health Insurance Portability and Accountability Act ([HIPAA](https://aws.amazon.com/compliance/hipaa-compliance/)). It can also be used for workloads that are compliant with the Payment Card Industry Data Security Standard ([PCI DSS](https://aws.amazon.com/compliance/pci-dss-level-1-faqs/)); the American Institute of CPAs (AICPA) Service Organization Control ([SOC](https://aws.amazon.com/compliance/soc-faqs/)); the International Organization for Standardization (ISO) and International Electrotechnical Commission (IEC) standards [ISO/IEC 27001](https://aws.amazon.com/compliance/iso-27001-faqs/), [ISO/IEC 27017](https://aws.amazon.com/compliance/iso-27017-faqs/), and [ISO/IEC 27018](https://aws.amazon.com/compliance/iso-27018-faqs/); and [ISO 9001](https://aws.amazon.com/compliance/iso-9001-faqs/).

**Amazon Shield**

**AWS Shield** is a managed distributed denial of service (DDoS) protection service that safeguards applications that run on AWS. It provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection.

AWS Shield helps protects your website from all types of DDoS attacks, including Infrastructure layer attacks (like User Datagram Protocol—or UDP—floods), state exhaustion attacks (like TCP SYN floods), and application-layer attacks (like HTTP GET or POST floods). For examples, see the [AWS WAF and AWS Shield Advanced Developer Guide](https://aws.amazon.com/documentation/waf/).

**AWS Shield Standard** is automatically enabled to all AWS customers at no additional cost.

**AWS Shield Advanced** is an optional paid service. AWS Shield Advanced provides additional protections against more sophisticated and larger attacks for your applications that run on Amazon EC2, Elastic Load Balancing, Amazon CloudFront, AWS Global Accelerator, and Amazon Route 53. AWS Shield Advanced is available to all customers. However, to contact the DDoS Response Team, customers need to have either Enterprise Support or Business Support from AWS Support.

**Section 5: Securing Data on AWS**

**Encryption of data at rest**

**Data encryption** is an essential tool to use when your objective is to protect digital data. Data encryption takes data that is legible and encodes it so that it is unreadable to anyone who does not have access to the secret key that can be used to decode it. Thus, even if an attacker gains access to your data, they cannot make sense of it. 

**Data at rest** refers to data that is physically stored on disk or on tape.

You can create encrypted file systems on AWS so that all your data and metadata is encrypted at rest by using the open standard Advanced Encryption Standard (AES)-256 encryption algorithm. When you use AWS KMS, encryption and decryption are handled automatically and transparently, so that you do not need to modify your applications. If your organization is subject to corporate or regulatory policies that require encryption of data and metadata at rest, AWS recommends  enabling encryption on all services that store your data. You can encrypt data stored in any service that is supported by AWS KMS.


**Encryption of data in transit**

**Data in transit** refers to data that is moving across the network. Encryption of data in transit is accomplished by using Transport Layer Security (TLS) 1.2 with an open standard AES-256 cipher. TLS was formerly called Secure Sockets Layer (SSL).

**AWS Certificate Manager** is a service that enables you to provision, manage, and deploy SSL or TLS certificates for use with AWS services and your internal connected resources. SSL or TLS certificates are used to secure network communications and establish the identity of websites over the internet, and also resources on private networks. With AWS Certificate Manager, you can request a certificate and then deploy it on AWS resources (such as load balancers or CloudFront distributions).  AWS Certificate Manager also handles certificate renewals.

Web traffic that runs over HTTP is not secure. However, traffic that runs over **Secure HTTP (HTTPS)** is encrypted by using TLS or SSL. HTTPS traffic is protected against eavesdropping and man-in-the-middle attacks because of the bidirectional encryption of the communication.

AWS services support encryption for data in transit.

**Securing Amazon S3 buckets and objects**

By default, all Amazon S3 buckets are private and can be accessed *only* by users who are explicitly granted access.  It is essential to manage and control access to Amazon S3 data. AWS provides many tools and options for controlling access to your S3 buckets or objects, including:

•Using **Amazon S3 Block Public Access**. These settings override any other policies or object permissions. Enable **Block Public Access** for all buckets that you don't want to be publicly accessible. This feature provides a straightforward method for avoiding unintended exposure of Amazon S3 data.

•

•Writing **IAM policies** that specify the users or roles that can access specific buckets and objects. This method was discussed in detail earlier in this module.

•

•Writing **bucket policies** that define access to specific buckets or objects.  This option is typically used when the user or system cannot authenticate by using IAM. Bucket policies can be configured to grant access across AWS accounts or to grant public or anonymous access to Amazon S3 data. If bucket policies are used, they should be written carefully and tested fully. You can specify a deny statement in a bucket policy to restrict access. Access will be restricted even if the users have permissions that are granted in an identity-based policy that is attached to the users.

•

•Setting **access control lists (ACLs)** on your buckets and objects. ACLs are less commonly used (ACLs predate IAM). If you do use ACLs, do not set access that is too open or permissive.

**AWS Trusted Advisor** provides a bucket permission check feature that is a useful tool for discovering if any of the buckets in your account have permissions that grant global access. 

**Section 6: Working to ensure compliance**

**AWS Config**

**AWS Config** is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. AWS Config continuously monitors and records your AWS resource configurations, and it enables you to automate the evaluation of recorded configurations against desired configurations. With AWS Config, you can review changes in configurations and relationships between AWS resources, review detailed resource configuration histories, and determine your overall compliance against the configurations that are specified in your internal guidelines. This enables you to simplify compliance auditing, security analysis, change management, and operational troubleshooting.

AWS Config is a Regional service. To track resources across Regions, enable it in every Region that you use. AWS Config offers an aggregator feature that can show an aggregated view of resources across multiple Regions and even multiple accounts.

**AWS Artifact**

**AWS Artifact** provides on-demand downloads of AWS security and compliance documents, such as AWS ISO certifications, Payment Card Industry (PCI), and Service Organization Control (SOC) reports. You can submit the security and compliance documents (also known as *audit artifacts*) to your auditors or regulators to demonstrate the security and compliance of the AWS infrastructure and services that you use. You can also use these documents as guidelines to evaluate your own cloud architecture and assess the effectiveness of your company's internal controls. AWS Artifact provides documents about AWS only. AWS customers are responsible for developing or obtaining documents that demonstrate the security and compliance of their companies.

You can also use AWS Artifact to review, accept, and track the status of AWS agreements such as the Business Associate Agreement (BAA). A BAA typically is required for companies that are subject to HIPAA to ensure that protected health information (PHI) is appropriately safeguarded. With AWS Artifact, you can accept agreements with AWS and designate AWS accounts that can legally process restricted information. You can accept an agreement on behalf of multiple accounts. To accept agreements for multiple accounts, use AWS Organizations to create an organization. 





**Additional Security Services and Resources**

**AWS Service Catalog** enables organizations to create and manage catalogs of IT services that are approved for use (for example, for your employees to use) on AWS. These IT services can include everything from virtual machine images, servers, software, and databases to complete multi-tier application architectures.

From the perspective of AWS Service Catalog, an IT service can be thought of as a product. A product could be a single compute instance that runs Amazon Linux, it could be a fully configured multi-tier web application that runs in its own environment, or it could be any other useful IT service that you build on AWS. This enables your users to quickly deploy the IT services that they need, and it is designed so that users deploy only approved configurations. AWS Service Catalog can support your efforts to centrally manage deployed IT services, and it can help you achieve consistent governance and meet compliance requirements.

**Amazon Macie** is a security service that uses machine learning to automatically discover, classify, and protect sensitive data in AWS. Amazon Macie recognizes sensitive data such as personally identifiable information (PII) or intellectual property. It provides you with dashboards and alerts that give visibility into how this data is being accessed or moved. Amazon Macie is a fully managed service that continuously monitors data access activity for anomalies, and it generates detailed alerts when it detects risk of unauthorized access or inadvertent data leaks. Amazon Macie is currently available to protect data that is stored in Amazon S3.

**Amazon Inspector** is an automated security assessment service that helps improve the security and compliance of applications that are deployed on AWS. Amazon Inspector automatically assesses applications for exposure, vulnerabilities, and deviations from best practices. After performing an assessment, Amazon Inspector produces a detailed list of security findings that are listed by level of severity. These findings can be reviewed directly or as part of detailed assessment reports that are available via the Amazon Inspector console or the API.

**Amazon GuardDuty** is a threat-detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts and workloads. With the cloud, the collection and aggregation of account and network activities is simplified, but it can be time-consuming for security teams to continuously analyze event log data for potential threats. GuardDuty uses machine learning, anomaly detection, and integrated threat intelligence to identify and rank potential threats. GuardDuty analyzes tens of billions of events across multiple AWS data sources, such as AWS CloudTrail, Amazon VPC Flow Logs, and Domain Name System (DNS) logs. 





**Module 5: Networking and Content Delivery**

**Section 1: Networking Basics**

**Classless Inter-Domain Routing (CIDR)**

A common method to describe networks is Classless Inter-Domain Routing (CIDR). The CIDR address is expressed as follows:

•An IP address (which is the first address of the network)

•Next, a slash character (/)

•Finally, a number that tells you how many bits of the routing prefix must be fixed or allocated for the network identifier

The bits that are not fixed are allowed to change. CIDR is a way to express a group of IP addresses that are consecutive to each other.

In this example, the CIDR address is 192.0.2.0/24. The last number (24) tells you that the first 24 bits must be fixed. The last 8 bits are flexible, which means that 28 (or 256) IP addresses are available for the network, which range from 192.0.2.0 to 192.0.2.255. The fourth decimal digit is allowed to change from 0 to 255.

If the CIDR was 192.0.2.0/16, the last number (16) tells you that the first 16 bits must be fixed. The last 16 bits are flexible, which means that 216 (or 65,536) IP addresses are available for the network, ranging from 192.0.0.0 to 192.0.255.255. The third and fourth decimal digits can each 

change from 0 to 255.

There are two special cases:

•Fixed IP addresses, in which every bit is fixed, represent a single IP address (for example, *192.0.2.0/32*). This type of address is helpful when you want to set up a firewall rule and give access to a specific host.

•The internet, in which every bit is flexible, is represented as 0.0.0.0/0

**Section 2: Amazon VPC**

**Amazon VPC**

Amazon Virtual Private Cloud (Amazon VPC) is a service that lets you provision a logically isolated section of the AWS Cloud (called a virtual private cloud, or VPC) where you can launch your AWS resources.

Amazon VPC gives you control over your virtual networking resources, including the selection of your own IP address range, the creation of subnets, and the configuration of route tables and network gateways. You can use both IPv4 and IPv6 in your VPC for secure access to resources and applications.

You can also customize the network configuration for your VPC. For example, you can create a public subnet for your web servers that can access the public internet. You can place your backend systems (such as databases or application servers) in a private subnet with no public internet access.

Finally, you can use multiple layers of security, including security groups and network access control lists (network ACLs), to help control access to Amazon Elastic Compute Cloud (Amazon EC2) instances in each subnet.

**VPCs and Subnets**

Amazon VPC enables you to provision virtual private clouds (VPCs). A *VPC* is a virtual network that is logically isolated from other virtual networks in the AWS Cloud. A VPC is dedicated to your account. VPCs belong to a single AWS Region and can span multiple Availability Zones.

After you create a VPC, you can divide it into one or more subnets. A *subnet* is a range of IP addresses in a VPC. Subnets belong to a single Availability Zone. You can create subnets in different Availability Zones for high availability. Subnets are generally classified as public or private. *Public subnets* have direct access to the internet, but *private subnets* do not.

**Reserved IP addresses**

When you create a subnet, it requires its own CIDR block. For each CIDR block that you specify, AWS reserves five IP addresses within that block, and these addresses are not available for use. AWS reserves these IP addresses for:

•Network address

•VPC local router (internal communications)

•Domain Name System (DNS) resolution

•Future use

•Network broadcast address

For example, suppose that you create a subnet with an IPv4 CIDR block of 10.0.0.0/24 (which has 256 total IP addresses). The subnet has 256 IP addresses, but only 251 are available because five are reserved.

**Public IP address types**

When you create a VPC, every instance in that VPC gets a private IP address automatically. You can also request a public IP address to be assigned when you create the instance by modifying the subnet’s auto-assign public IP address properties.

An *Elastic IP address* is a static and public IPv4 address that is designed for dynamic cloud computing. You can associate an Elastic IP address with any instance or network interface for any VPC in your account. With an Elastic IP address, you can mask the failure of an instance by rapidly remapping the address to another instance in your VPC. Associating the Elastic IP address with the network interface has an advantage over associating it directly with the instance. You can move all of the attributes of the network interface from one instance to another in a single step.

Additional costs might apply when you use Elastic IP addresses, so it is important to release them when you no longer need them. 

**Elastic Network Interface**

An *elastic network interface* is a virtual network interface that you can attach or detach from an instance in a VPC. A network interface's attributes follow it when it is reattached to another instance. When you move a network interface from one instance to another, network traffic is redirected to the new instance.

Each instance in your VPC has a default network interface (the primary network interface) that is assigned a private IPv4 address from the IPv4 address range of your VPC. You cannot detach a primary network interface from an instance. You can create and attach an additional network interface to any instance in your VPC. The number of network interfaces you can attach varies by instance type. 

**Route tables and routes**

A *route table* contains a set of rules (called *routes*)** that directs network traffic from your subnet. Each route specifies a *destination* and a *target*. The *destination* is the destination CIDR block where you want traffic from your subnet to go. The *target* is the target that the destination traffic is sent through. By default, every route table that you create contains a *local route* for communication in the VPC. You can customize route tables by adding routes. You cannot delete the local route entry that is used for internal communications.

Each subnet in your VPC must be associated with a route table. The *main route table* is the route table is automatically assigned to your VPC. It controls the routing for all subnets that are not explicitly associated with any other route table. A subnet can be associated with only one route table at a time, but you can associate multiple subnets with the same route table. 







**Section 3: VPC Networking**

**Internet Gateway**

An *internet gateway*** is a scalable, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. An internet gateway serves two purposes: to provide a target in your VPC route tables for internet-routable traffic, and to perform network address translation for instances that were assigned public IPv4 addresses.

To make a subnet *public*, you attach an *internet gateway* to your VPC and add a route to the route table to send non-local traffic through the internet gateway to the internet (0.0.0.0/0). 

**Network Address Translation (NAT) Gateway**

A *network address translation (NAT) gateway* enables instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating a connection with those instances.

To create a NAT gateway, you must specify the public subnet in which the NAT gateway should reside. You must also specify an Elastic IP address to associate with the NAT gateway when you create it. After you create a NAT gateway, you must update the route table that is associated with one or more of your private subnets to point internet-bound traffic to the NAT gateway. Thus, instances in your private subnets can communicate with the internet.

You can also use a NAT instance in a public subnet in your VPC instead of a NAT gateway. However, a NAT gateway is a managed NAT service that provides better availability, higher bandwidth, and less administrative effort. For common use cases, AWS recommends that you use a NAT gateway instead of a NAT instance. 

**VPC Sharing**

VPC sharing enables customers to share subnets with other AWS accounts in the same organization in AWS Organizations. VPC sharing enables multiple AWS accounts to create their application resources—such as Amazon EC2 instances, Amazon Relational Database Service (Amazon RDS) databases, Amazon Redshift clusters, and AWS Lambda functions—into shared, centrally managed VPCs. In this model, the account that owns the VPC (owner) shares one or more subnets with other accounts (participants) that belong to the same organization in AWS Organizations. After a subnet is shared, the participants can view, create, modify, and delete their application resources in the subnets that are shared with them. Participants cannot view, modify, or delete resources that belong to other participants or the VPC owner.

VPC sharing offers several benefits:

•Separation of duties – Centrally controlled VPC structure, routing, IP address allocation

•Ownership – Application owners continue to own resources, accounts, and security groups

•Security groups – VPC sharing participants can reference the security group IDs of each other

•Efficiencies – Higher density in subnets, efficient use of VPNs and AWS Direct Connect

•No hard limits – Hard limits can be avoided—for example, 50 virtual interfaces per AWS Direct Connect connection through simplified network architecture

•Optimized costs – Costs can be optimized through the reuse of NAT gateways, VPC interface endpoints, and intra-Availability Zone traffic

VPC sharing enables you to decouple accounts and networks. You have fewer, larger, centrally managed VPCs. Highly interconnected applications automatically benefit from this approach.

**VPC Peering**

A *VPC peering connection* is a networking connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.

When you set up the peering connection, you create rules in your route table to allow the VPCs to communicate with each other through the peering resource. 

**AWS Site-to-Site VPN**

By default, instances that you launch into a VPC cannot communicate with a remote network. To connect your VPC to your remote network (that is, create a virtual private network or VPN connection), you:

1\.Create a new virtual gateway device (called a *virtual private network (VPN) gateway*) and attach it to your VPC.

2\.Define the configuration of the VPN device or the *customer gateway*. The customer gateway is not a device but an AWS resource that provides information to AWS about your VPN device.

3\.Create a custom route table to point corporate data center-bound traffic to the VPN gateway. You also must update security group rules. (You will learn about security groups in the next section.)

4\.Establish an *AWS Site-to-Site VPN (Site-to-Site VPN) connection* to link the two systems together.

5\.Configure routing to pass traffic through the connection. 

**AWS Direct Connect**

One of the challenges of network communication is network performance. Performance can be negatively affected if your data center is located far away from your AWS Region. For such situations, AWS offers AWS Direct Connect, or DX. *AWS Direct Connect* enables you to establish a dedicated, private network connection between your network and one of the DX locations. This private connection can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections. DX uses open standard 802.1q virtual local area networks (VLANs).

**VPC Endpoints**

A *VPC endpoint* is a virtual device that enables you to privately connect your VPC to supported AWS services and VPC endpoint services that are powered by AWS PrivateLink. Connection to these services does not require an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

There are two types of VPC endpoints:

•An *interface VPC endpoint* (interface endpoint) enables you to connect to services that are powered by AWS PrivateLink. These services include some AWS services, services that are hosted by other AWS customers and AWS Partner Network (APN) Partners in their own VPCs (referred to as *endpoint services*), and supported AWS Marketplace APN Partner services. The owner of the service is the *service provider*, and you—as the principal who creates the interface endpoint—are the *service consumer*. You are charged for creating and using an interface endpoint to a service. Hourly usage rates and data processing rates apply. See the AWS 

Documentation for a list of supported[ ](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html)[interface endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html).

•Gateway endpoints: The use of gateway endpoints incurs no additional charge. Standard charges for data transfer and resource usage apply. 

**AWS Transit Gateway**

You can configure your VPCs in several ways, and take advantage of numerous connectivity options and gateways. These options and gateways include AWS Direct Connect (via DX gateways), NAT gateways, internet gateways, VPC peering, etc. It is not uncommon to find AWS customers with hundreds of VPCs distributed across AWS accounts and Regions to serve multiple lines of business, teams, projects, and so forth. Things get more complex when customers start to set up connectivity between their VPCs. All the connectivity options are strictly point-to-point, so the number of VPC-to-VPC connections can grow quickly. As you grow the number of workloads that run on AWS, you must be able to scale your networks across multiple accounts and VPCs to keep up with the growth.

Though you can use VPC peering to connect pairs of VPCs, managing point-to-point connectivity across many VPCs without the ability to centrally manage the connectivity policies can be operationally costly and difficult. For on-premises connectivity, you must attach your VPN to each individual VPC. This solution can be time-consuming to build and difficult to manage when the number of VPCs grows into the hundreds.

To solve this problem, you can use AWS Transit Gateway to simplify your networking model. With AWS Transit Gateway, you only need to create and manage a single connection from the central gateway into each VPC, on-premises data center, or remote office across your network. 

A transit gateway acts as a hub that controls how traffic is routed among all the connected networks, which act like spokes. This hub-and-spoke model significantly simplifies management and reduces operational costs because each network only needs to connect to the transit gateway and not to every other network. Any new VPC is connected to the transit gateway, and is then automatically available to every other network that is connected to the transit gateway. This ease of connectivity makes it easier to scale your network as you grow.

**Section 4: VPC Security**

**Security Groups**

A *security group* acts as a virtual firewall for your instance, and it controls inbound and outbound traffic. Security groups act at the instance level, not the subnet level. Therefore, each instance in a subnet in your VPC can be assigned to a different set of security groups.



At the most basic level, a security group is a way for you to filter traffic to your instances.

Security groups have *rules* that control the inbound and outbound traffic. When you create a security group, it has no inbound rules. Therefore, *no inbound traffic that originates from another host to your instance is allowed* until you add inbound rules to the security group. By default, a security group includes an outbound rule that *allows all outbound traffic*. You can remove the rule and add outbound rules that allow specific outbound traffic only. If your security group has no outbound rules, no outbound traffic that originates from your instance is allowed.

Security groups are *stateful*, which means that state information is kept even after a request is processed. Thus, if you send a request from your instance, the response traffic for that request is allowed to flow in regardless of inbound security group rules. Responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules. 

When you create a custom security group, you can specify allow rules, but not deny rules. All rules are evaluated before the decision to allow traffic.

**Network Access Control Lists (Network ACLs)**

A *network access control list (network ACL)*** is an optional layer of security for your Amazon VPC. It acts as a firewall for controlling traffic in and out of one or more subnets. To add another layer of security to your VPC, you can set up network ACLs with rules that are similar to your security groups.

Each subnet in your VPC must be associated with a network ACL. If you don't explicitly associate a subnet with a network ACL, the subnet is automatically associated with the default network ACL. You can associate a network ACL with multiple subnets; however, a subnet can be associated with only one network ACL at a time. When you associate a network ACL with a subnet, the previous association is removed. 

A network ACL has separate inbound and outbound rules, and each rule can either allow or deny traffic. Your VPC automatically comes with a modifiable default network ACL. By default, it allows all inbound and outbound IPv4 traffic and, if applicable, IPv6 traffic. 

Network ACLs are *stateless*, which means that no information about a request is maintained after a request is processed. 

You can create a custom network ACL and associate it with a subnet. By default, each custom network ACL denies all inbound and outbound traffic until you add rules. 

A network ACL contains a numbered list of rules that are evaluated in order, starting with the lowest numbered rule. The purpose is to determine whether traffic is allowed in or out of any subnet that is associated with the network ACL. The highest number that you can use for a rule is 32,766. AWS recommends that you create rules in increments (for example, increments of 10 or 100) so that you can insert new rules where you need them later. 

Here is a summary of the differences between security groups and network ACLs:

•Security groups** act at the instance level, but network ACLs act at the subnet level.

•Security groups support allow rules only, but network ACLs support both allow and deny rules.

•Security groups are stateful, but network ACLs are stateless.

For security groups, all rules are evaluated before the decision is made to allow traffic. For network ACLs, rules are evaluated in number order before the decision is made to allow traffic.

**Section 5: Amazon Route 53**

**Amazon Route 53**

Amazon Route 53 is a highly available and scalable cloud[ ](https://aws.amazon.com/route53/what-is-dns/)[Domain Name System (DNS)](https://aws.amazon.com/route53/what-is-dns/) web service. It is designed to give developers and businesses a reliable and cost-effective way to route users to internet applications by translating names (like *www.example.com*) into the numeric IP addresses (like *192.0.2.1*) that computers use to connect to each other. In addition, Amazon Route 53 is fully compliant with IPv6.

Amazon Route 53 effectively connects user requests to infrastructure running in AWS—such as Amazon EC2 instances, Elastic Load Balancing load balancers, or Amazon S3 buckets—and can also be used to route users to infrastructure that is outside of AWS.

You can use Amazon Route 53 to configure DNS health checks so you that can route traffic to healthy endpoints or independently monitor the health of your application and its endpoints.

Amazon Route 53 traffic flow helps you manage traffic globally through several routing types, which can be combined with DNS failover to enable various low-latency, fault-tolerant architectures. You can use Amazon Route 53 traffic flow’s simple visual editor to manage how your users are routed to your application’s endpoints—whether in a single AWS Region or distributed around the globe.

Amazon Route 53 also offers Domain Name Registration—you can purchase and manage domain names (like *example.com*), and Amazon Route 53 will automatically configure DNS settings for your domains.

**Amazon Route 53 Supported Routing**

Amazon Route 53 supports several types of routing policies, which determine how Amazon Route 53 responds to queries:

•*Simple routing (round robin)* – Use for a single resource that performs a given function for your domain (such as a web server that serves content for the example.com website).

•*Weighted round robin routing –* Use to route traffic to multiple resources in proportions that you specify. Enables you to assign weights to resource record sets to specify the frequency with which different responses are served. You might want to use this capability to do A/B testing, which is when you send a small portion of traffic to a server where you made a software change. For instance, suppose you have two record sets that are associated with one DNS name: one with weight 3 and one with weight 1. In this case, 75 percent of the time, Amazon Route 53 will return the record set with weight 3, and 25 percent of the time, Amazon Route 53 will return the record set with weight 1. Weights can be any number between 0 and 255.

•*Latency routing (LBR) –* Use when you have resources in multiple AWS Regions and you want to route traffic to the Region that provides the best latency. Latency routing works by routing your customers to the AWS endpoint (for example, Amazon EC2 instances, Elastic IP addresses, or load balancers) that provides the fastest experience based on actual performance measurements of the different AWS Regions where your application runs.

•*Geolocation routing –* Use when you want to route traffic based on the location of your users. When you use geolocation routing, you can localize your content and present some or all of your website in the language of your users. You can also use geolocation routing to restrict the distribution of content to only the locations where you have distribution rights. Another possible use is for balancing the load across endpoints in a predictable, easy-to-manage way, so that each user location is consistently routed to the same endpoint.

•*Geoproximity routing* – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.

•*Failover routing (DNS failover) –* Use when you want to configure active-passive failover. Amazon Route 53 can help detect an outage of your website and redirect your users to alternate locations where your application is operating properly. When you enable this feature, Amazon Route 53 health-checking agents will monitor each location or endpoint of your application to determine its availability. You can take advantage of this feature to increase the availability of your customer-facing application.

•*Multivalue answer routing* – Use when you want Route 53 to respond to DNS queries with up to eight healthy records that are selected at random. You can configure Amazon Route 53 to return multiple values—such as IP addresses for your web servers—in response to DNS queries. You can specify multiple values for almost any record, but multivalue answer routing also enables you to check the health of each resource so that Route 53 returns only values for healthy resources. It's not a substitute for a load balancer, but the ability to return multiple health-checkable IP addresses is a way to use DNS to improve availability and load balancing. 

**Amazon Route 53 DNS Failover**

Amazon Route 53 enables you to improve the availability of your applications that run on AWS by:

•Configuring backup and failover scenarios for your own applications.

•Enabling highly available multi-Region architectures on AWS.

•Creating health checks to monitor the health and performance of your web applications, web servers, and other resources. Each health check that you create can monitor one of the following—the health of a specified resource, such as a web server; the status of other health checks; and the status of an Amazon CloudWatch alarm.

You can do the following tasks with Route 53 to ensure high availability:

1\.Create two DNS records for the Canonical Name Record (CNAME) *www* with a routing policy of *Failover Routing*. The first record is the primary route policy, which points to the load balancer for your web application. The second record is the secondary route policy, which points to your static Amazon S3 website.

2\.Use Route 53 health checks to make sure that the primary is running. If it is, all traffic defaults to your web application stack. Failover to the static backup site would be triggered if either the web server goes down (or hangs), or the database instance goes down.

**Section 6: Amazon CloudFront**

**Content Delivery Network (CDN)**

A content delivery network (CDN) is a globally distributed system of caching servers. A CDN caches copies of commonly requested files (static content, such as Hypertext Markup Language, or HTML; Cascading Style Sheets, or CSS; JavaScript; and image files) that are hosted on the application origin server. The CDN delivers a local copy of the requested content from a cache edge or Point of Presence that provides the fastest delivery to the requester.

CDNs also deliver dynamic content that is unique to the requester and is not cacheable. Having a CDN deliver dynamic content improves application performance and scaling. The CDN establishes and maintains secure connections closer to the requester. If the CDN is on the same network as the origin, routing back to the origin to retrieve dynamic content is accelerated. In addition, content such as form data, images, and text can be ingested and sent back to the origin, thus taking advantage of the low-latency connections and proxy behavior of the PoP. 

**Amazon CloudFront**

Amazon CloudFront is a fast CDN service that securely delivers data, videos, applications, and application programming interfaces (APIs) to customers globally with low latency and high transfer speeds. It also provides a developer-friendly environment. Amazon CloudFront delivers files to users over a global network of edge locations and Regional edge caches. 

Amazon CloudFront is different from traditional content delivery solutions because it enables you to quickly obtain the benefits of high-performance content delivery without negotiated contracts, high prices, or minimum fees. Like other AWS services, Amazon CloudFront is a self-service offering with pay-as-you-go pricing.

**Amazon CloudFront Infrastructure**

Amazon CloudFront delivers content through a worldwide network of data centers that are called *edge locations*. When a user requests content that you serve with CloudFront, the user is routed to the edge location that provides the lowest latency (or time delay) so that content is delivered with the best possible performance. CloudFront edge locations are designed to serve popular content quickly to your viewers.

As objects become less popular, individual edge locations might remove those objects to make room for more popular content. For the less popular content, CloudFront has *Regional edge caches.* Regional edge caches are CloudFront locations that are deployed globally and are close to your viewers. They are located between your origin server and the global edge locations that serve content directly to viewers. 

A Regional edge cache has a larger cache than an individual edge location, so objects remain in the Regional edge cache longer. More of your content remains closer to your viewers, which reduces the need for CloudFront to go back to your origin server and improves overall performance for viewers. 







**Amazon CloudFront Benefits**

Amazon CloudFront provides the following benefits:

•*Fast and global* – Amazon CloudFront is massively scaled and globally distributed. To deliver content to end users with low latency, Amazon CloudFront uses a global network that consists of edge locations and regional caches.

•*Security at the edge* – Amazon CloudFront provides both network-level and application-level protection. Your traffic and applications benefit through various built-in protections, such as AWS Shield Standard, at no additional cost. You can also use configurable features, such as AWS Certificate Manager (ACM), to create and manage custom Secure Sockets Layer (SSL) certificates at no extra cost.

•*Highly programmable* – Amazon CloudFront features can be customized for specific application requirements. It integrates with Lambda@Edge so that you can run custom code across AWS locations worldwide, which enables you to move complex application logic closer to users to improve responsiveness. The CDN also supports integrations with other tools and automation interfaces for DevOps. It offers continuous integration and continuous delivery (CI/CD) environments.

•*Deeply integrated with AWS* – Amazon CloudFront is integrated with AWS, with both physical locations that are directly connected to the AWS Global Infrastructure and other AWS services. You can use APIs or the AWS Management Console to programmatically configure all features in the CDN.

•*Cost-effective* – Amazon CloudFront is cost-effective because it has no minimum commitments and charges you only for what you use. Compared to self-hosting, Amazon CloudFront avoids the expense and complexity of operating a network of cache servers in multiple sites across the internet. It eliminates the need to overprovision capacity to serve potential spikes in traffic. Amazon CloudFront also uses techniques like collapsing simultaneous viewer requests at an edge location for the same file into a single request to your origin server. The result is reduced load on your origin servers and reduced need to scale your origin infrastructure, which can result in further cost savings. If you use AWS origins such as Amazon Simple Storage Service (Amazon S3) or Elastic Load Balancing, you pay only for storage costs, not for any data transferred between these services and CloudFront.

**Amazon CloudFront Pricing**

Amazon CloudFront charges are based on actual usage of the service in four areas:

•*Data transfer out –* You are charged for the volume of data that is transferred out from Amazon CloudFront edge locations, measured in GB, to the internet or to your origin (both AWS origins and other origin servers). Data transfer usage is totaled separately for specific geographic regions, and then cost is calculated based on pricing tiers for each area. If you use other AWS services as the origins of your files, you are charged separately for your use of those services, including storage and compute hours.

•*HTTP(S) requests –* You are charged for the number of HTTP(S) requests that are made to Amazon CloudFront for your content.

•*Invalidation requests –* You are charged per path in your invalidation request. A path that is listed in your invalidation request represents the URL (or multiple URLs if the path contains a wildcard character) of the object that you want to invalidate from CloudFront cache. You can request up to 1,000 paths each month from Amazon CloudFront at no additional charge. Beyond the first 1,000 paths, you are charged per path that is listed in your invalidation requests.

•*Dedicated IP custom Secure Sockets Layer (SSL) –* You pay $600 per month for each custom SSL certificate that is associated with one or more CloudFront distributions that use the Dedicated IP version of custom SSL certificate support. This monthly fee is prorated by the hour. For example, if your custom SSL certificate was associated with at least one CloudFront distribution for just 24 hours (that is, 1 day) in the month of June, your total charge for using the custom SSL certificate feature in June is (1 day / 30 days) \* $600 = $20.

**Module 6: Compute**

**Section 1: Compute Services Overview**

**Amazon Compute Services**

Amazon Web Services (AWS) offers many compute services. Here is a brief summary of what each compute service offers:

•**Amazon Elastic Compute Cloud** **(Amazon EC2)** provides resizable virtual machines.

•**Amazon EC2 Auto Scaling** supports application availability by allowing you to define conditions that will automatically launch or terminate EC2 instances.

•**Amazon Elastic Container Registry** **(Amazon ECR)** is used to store and retrieve Docker images.

•**Amazon Elastic Container Service (Amazon ECS)** is a container orchestration service that supports Docker.

•**VMware Cloud on AWS** enables you to provision a hybrid cloud without custom hardware.

•**AWS Elastic Beanstalk** provides a simple way to run and manage web applications.

•**AWS Lambda** is a serverless compute solution. You pay only for the compute time that you use.

•**Amazon Elastic Kubernetes Service (Amazon EKS)** enables you to run managed Kubernetes on AWS.

•**Amazon Lightsail** provides a simple-to-use service for building an application or website.

•**AWS Batch** provides a tool for running batch jobs at any scale.

•**AWS Fargate** provides a way to run containers that reduce the need for you to manage servers or clusters.

•**AWS Outposts** provides a way to run select AWS services in your on-premises data center.

•**AWS Serverless Application Repository** provides a way to discover, deploy, and publish serverless applications.

**Categorizing Compute Services**

You can think of each AWS compute service as belonging to one of four broad categories: virtual machines (VMs) that provide infrastructure as a service (IaaS), serverless, container-based, and platform as a service (PaaS).

**Amazon EC2** provides virtual machines, and you can think of it as infrastructure as a service (IaaS). IaaS services provide flexibility and leave many of the server management responsibilities to you. You choose the operating system, and you also choose the size and resource capabilities of the servers that you launch. For IT professionals who have experience using on-premises computing, virtual machines are a familiar concept. Amazon EC2 was one of the first AWS services, and it remains one of the most popular services.



**AWS Lambda** is a zero-administration compute platform. AWS Lambda enables you to run code without provisioning or managing servers. You pay only for the compute time that is consumed. This serverless technology concept is relatively new to many IT professionals. However, it is becoming more popular because it supports cloud-native architectures, which enable massive scalability at a lower cost than running servers 24/7 to support the same workloads.



Container-based services—including **Amazon Elastic Container Service, Amazon Elastic Kubernetes Service, AWS Fargate, and Amazon Elastic Container Registry***—*enable you to run multiple workloads on a single operating system (OS). Containers spin up more quickly than virtual machines, thus offering responsiveness. Container-based solutions continue to grow in popularity.

Finally, **AWS Elastic Beanstalk** provides a platform as a service (PaaS). It facilitates the quick deployment of applications that you create by providing all the application services that you need. AWS manages the OS, the application server, and the other infrastructure components so that you can focus on developing your application code. 

**Choosing the Optimal Compute Service**

Often, the compute architecture that you use is determined by legacy code. However, that does not mean that you cannot evolve the architecture to take advantage of proven cloud-native designs.


Best practices include:

•Evaluate the available compute options

•Understand the available compute configuration options

•Collect computer-related metrics

•Use the available elasticity of resources

•Re-evaluate compute needs based on metrics

Sometimes, a customer will start with one compute solution and decide to change the design based on their analysis of metrics. 

**Section 2: Amazon EC2**

**Amazon Elastic Compute Cloud (Amazon EC2)**

**Running servers on-premises** is an expensive undertaking. Hardware must be procured, and this procurement can be based on project plans instead of the reality of how the servers are used. Data centers are expensive to build, staff, and maintain. Organizations also need to permanently provision a sufficient amount of hardware to handle traffic spikes and peak workloads. After traditional on-premises deployments are built, server capacity might be unused and idle for a significant portion of the time that the servers are running, which is wasteful.

Amazon Elastic Compute Cloud (Amazon EC2) provides virtual machines where you can host the same kinds of applications that you might run on a traditional on-premises server. It provides secure, resizable compute capacity in the cloud. EC2 instances can support a variety of workloads. Common uses for EC2 instances include, but are not limited to:



•Application servers

•Web servers

•Database servers

•Game servers

•Mail servers

•Media servers

•Catalog servers

•File servers

•Computing servers

Proxy servers

**Amazon EC2 Overview**

The **EC2** in Amazon EC2 stands for **Elastic Compute Cloud***:*

•**Elastic** refers to the fact that you can easily increase or decrease the number of servers you run to support an application automatically, and you can also increase or decrease the size of existing servers.

•**Compute** refers to reason why most users run servers in the first place, which is to host running applications or process data—actions that require compute resources, including processing power (CPU) and memory (RAM).

•**Cloud** refers to the fact that the EC2 instances that you run are hosted in the cloud.

Amazon EC2 provides virtual machines in the cloud and gives you full administrative control over the Windows or Linux operating system that runs on the instance. Most server operating systems are supported, including: Windows 2008, 2012, 2016, and 2019, Red Hat, SuSE, Ubuntu, and Amazon Linux.

An operating system that runs on a virtual machine is often called *a guest operating system* to distinguish it from the *host* operating system. The host operating system is directly installed on any server hardware that hosts one or more virtual machines.

**Launching an Amazon EC2 Instance**

The first time you launch an Amazon EC2 instance, you will likely use the AWS Management Console Launch Instance Wizard. 

The **Launch Instance Wizard** makes it easy to launch an instance. For example, if you choose to accept all the default settings, you can skip most of the steps that are provided by the wizard and launch an EC2 instance in as few as six clicks.

However, for most deployments you will want to modify the default settings so that the servers you launch are deployed in a way that matches your specific needs.

**Select an AMI**

An **Amazon Machine Image (AMI)** provides information that is required to launch an **EC2** **instance**. You must specify a source AMI when you launch an instance. You can use different AMIs to launch different types of instances. For example, you can choose one AMI to launch an instance that will become a web server and another AMI to deploy an instance that will host an application server. You can also launch multiple instances from a single AMI.

An AMI includes the following components:

•A **template for the root volume** of the instance. A root volume typically contains an operating system (OS) and everything that was installed in that OS (applications, libraries, etc.). Amazon EC2 copies the template to the root volume of a new EC2 instance, and then starts it.

•**Launch permissions** that control which AWS accounts can use the AMI.

•A **block device mapping** that specifies the volumes to attach to the instance (if any) when it is launched.

You can choose many AMIs:

•**Quick Start –** AWS offers a number of pre-built AMIs for launching your instances. These AMIs include many Linux and Windows options.

•**My AMIs –** These AMIs are AMIs that you created.

•**AWS Marketplace –** The AWS Marketplace offers a digital catalog that lists thousands of software solutions. These AMIs can offer specific use cases to help you get started quickly.

•**Community AMIs –** These AMIs are created by people all around the world. These AMIs are not checked by AWS, so use them at your own risk. Community AMIs can offer many different solutions to various problems, but use them with care. Avoid using them in any production or corporate environment.

An AMI is created from an EC2 instance. You can **import** a virtual machine so that it becomes an EC2 instance, and then save the EC2 instance as an AMI. You can then launch an EC2 instance from that AMI. Alternatively, you can start with an **existing AMI**—such as of the Quick Start AMIs provided by AWS—and create an EC2 instance from it.

Regardless of which options you chose (step 1), you will have what the diagram refers to as *an unmodified instance*. From that instance, you might then create a *golden instance*—that is, a virtual machine that you configured with the specific OS and application settings that you want (step 2)—and then capture that as a new AMI (step 3). When you create an AMI, Amazon EC2 stops the instance, creates a snapshot of its root volume, and finally registers the snapshot as an AMI.

After an AMI is registered, the AMI can be used to launch new instances in the same AWS Region. The new AMI can now be thought of as a new starter AMI. You might want to also copy the AMI to other Regions (step 4), so that EC2 instances can also be launched in those locations. 


**Select an Instance Type**

After you choose the AMI for launching the instance, you must choose on an instance type.

Amazon EC2 provides a selection of **instance types** that optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity. The different instance types give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes, which enable you to scale your resources to the requirements of your target workload.

**Instance type categories** include general purpose, compute optimized, memory optimized, storage optimized, and accelerated computing instances. Each instance type category offers many instance types to choose from. 

**EC2 Instance Type Naming and Sizes**

When you look at an EC2 instance type, you will see that its name has several parts. For example, consider the T type.

T is the **family** **name**, which is then followed by a number. Here, that number is 3.

The number is the **generation** **number** of that type. So, a t3 instance is the third generation of the T family. In general, instance types that are of a higher generation are more powerful and provide a better value for the price.



The next part of the name is the **size** portion of the instance. When you compare sizes, it is important to look at the coefficient portion of the size category.



For example, a **t3.2xlarge** has twice the vCPU and memory of a **t3.xlarge**. The t3.xlarge has, in turn, twice the vCPU and memory of a t3.large.



It is also important to note that **network bandwidth** is also tied to the size of the Amazon EC2 instance. If you will run jobs that will be very network-intensive, you might be required to increase the instance specifications to meet your needs.

**Instance types** vary in several ways, including: CPU type, CPU or core count, storage type, storage amount, memory amount, and network performance. The chart provides a high-level view of the different instance categories, and which instance type families and generation numbers fit into each category type. Consider a few of the instance types in more detail:

•**T3** instances provide burstable performance **general purpose** instances that provide a baseline level of CPU performance with the ability to burst above the baseline. Use cases for this type of instance include websites and web applications, development environments, build servers, code repositories, microservices, test and staging environments, and line-of-business applications.

•**C5** instances are optimized for **compute-intensive** workloads, and deliver cost-effective high performance at a low price per compute ratio. Use cases include scientific modeling, batch processing, ad serving, highly scalable multiplayer gaming, and video encoding.

•**R5** instances are optimized for memory-intensive applications. Use cases include high-performance databases, data mining and analysis, in-memory databases, distributed web-scale in-memory caches, applications that perform real-time processing of unstructured big data, Apache Hadoop or Apache Spark clusters, and other enterprise applications.

In addition to considering the CPU, RAM, and storage needs of your workloads, it is also important to consider your network bandwidth requirements.

Each instance type provides a documented network performance level. For example, an a1.medium instance will provide up to 10 Gbps, but a p3dn.24xlarge instance provides up to 100 Gbps. Choose an instance type that meets your requirements.

When you launch multiple new EC2 instances, Amazon EC2 attempts to place the instances so that they are spread out across the underlying hardware by default. It does this to minimize correlated failures. However, if you want to specify specific placement criteria, you can use **placement groups** to influence the placement of a group of **interdependent** instances to meet the needs of your workload. For example, you might specify that three instances should all be deployed in the same Availability Zone to ensure lower network latency and higher network throughput between instances. See the[ ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)[Placement Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html) documentation for details.

Many instance types also enable you to configure enhanced networking to get significantly higher packet per second (PPS) performance, lower delay variation in the arrival of packets over the network (network jitter), and lower latencies. 

**Specify Network Settings**

After you have choose an AMI and an instance type, you must specify the network location where the EC2 instance will be deployed. The choice of **Region** must be made before you start the Launch Instance Wizard. Verify that you are in the correct Region page of the Amazon EC2 console before you choose **Launch Instance**.

When you launch an instance in a **default VPC**, AWS will assign it a **public IP** **address** by default. When you launch an instance into a **nondefault VPC**, the subnet has an attribute that determines whether instances launched into that subnet receive a public IP address from the public IPv4 address pool. By default, AWS will not assign a public IP address to instances that are launched in a nondefault subnet. You can control whether your instance receives a public IP address by either modifying the public IP addressing attribute of your subnet, or by enabling or disabling the public IP addressing feature during launch (which overrides the subnet's public IP addressing attribute). 

**Attach IAM Role (optional)**

It is common to use EC2 instances to run an application that must make secure API calls to other AWS services. To support these use cases, AWS enables you to **attach an AWS Identity and Access Management (IAM) role to an EC2 instance**. Without this feature, you might be tempted to place AWS credentials on an EC2 instance so an application that runs on that instance to use. However, you should never store AWS credentials on an EC2 instance. It is highly insecure. Instead, attach an IAM role to the EC2 instance. The IAM role then grants permission to make application programming interface (API) requests to the applications that run on the EC2 instance.

An **instance profile** is a container for an IAM role. If you use the AWS Management Console to create a role for Amazon EC2, the console automatically creates an instance profile and gives it the same name as the role. When you then use the Amazon EC2 console to launch an instance with an IAM role, you can select a role to associate with the instance. In the console, the list that displays is actually a list of instance profile names. 

You can attach an IAM role when you launch the instance, but you can also attach a role to an already running EC2 instance. When you define a role that can be used by an EC2 instance, you define which accounts or AWS services can assume the role. You also define which API actions and resources the application can use after it assumes the role. If you change a role, the change is propagated to all instances that have the role attached to them.

**User Data Script (optional)**

When you create your EC2 instances, you have the option of passing **user data** to the instance. User data can automate the completion of installations and configurations at instance launch. 

**Specify Storage**

When you launch an EC2 instance, you can configure storage options. For example, you can configure the size of the root volume where the guest operating system is installed. You can also attach additional storage volumes when you launch the instance. Some AMIs are also configured to launch more than one storage volume by default to provide storage that is separate from the root volume.

For each volume that your instance will have, you can specify the size of the disks, the volume types, and whether the storage will be retained if the instance is terminated. You can also specify if encryption should be used.


**Amazon EC2 Storage Options**

**Amazon Elastic Block Store (Amazon EBS)** is an easy-to-use, high-performance **durable block storage** service that is designed to be used with Amazon EC2 for both throughput- and transaction-intensive workloads. With Amazon EBS, you can choose from four different volume types to balance the optimal price and performance. You can change volume types or increase volume size without disrupting your critical applications, so you can have cost-effective storage when you need it.

**Amazon EC2 Instance Store** provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. Instance Store works well when you must temporarily store information that changes frequently, such as buffers, caches, scratch data, and other temporary content. You can also use Instance Store for data that is replicated across a fleet of instances, such as a load balanced pool of web servers. If the instances are stopped—either because of user error or a malfunction—the data on the instance store will be deleted.

**Amazon Elastic File System (Amazon EFS)** provides a simple, scalable, fully managed elastic Network File System (NFS) file system for use with AWS Cloud services and on-premises resources. It is built to scale on-demand to petabytes without disrupting applications. It grows and shrinks automatically as you add and remove files, which reduces the need to provision and manage capacity to accommodate growth.

**Amazon Simple Storage Service (Amazon S3)** is an object storage service that offers scalability, data availability, security, and performance. You can store and protect any amount of data for a variety of use cases, such as websites, mobile apps, backup and restore, archive, enterprise applications, Internet of Things (IoT) devices, and big data analytics.

**Add Tags**

A tag is a label that you assign to an AWS resource. Each tag consists of a *key* and an optional *value*, both of which you define. Tags enable you to categorize AWS resources, such as EC2 instances, in different ways. For example, you might tag instances by purpose, owner, or environment. 

Tagging is how you can attach metadata to an EC2 instance.

Tag keys and tag values are case-sensitive. For example, a commonly used tag for EC2 instances is a tag key that is called *Name* and a tag value that describes the instance, such as *My Web Server*. The *Name* tag is exposed by default in the Amazon EC2 console **Instances** page. However, if you create a key that is called *name* (with lower-case *n*), it will not appear in the **Name** column for the list of instances (though it will still appear in the instance details panel in the **Tags** tab).

It is a best practice to develop[ ](https://aws.amazon.com/answers/account-management/aws-tagging-strategies/)[Tagging strategies](https://aws.amazon.com/answers/account-management/aws-tagging-strategies/). Using a consistent set of tag keys makes it easier for you to manage your resources. You can also search and filter the resources based on the tags that you add.

**Security Group Settings**

A **security group** acts as a virtual firewall that controls network traffic for one or more instances. When you launch an instance, you can specify one or more security groups; otherwise, the default security group is used.

You can add **rules** to each security group. Rules allow traffic to or from its associated instances. You can modify the rules for a security group at any time, and the new rules will be automatically applied to all instances that are associated with the security group. When AWS decides whether to allow traffic to reach an instance, all the rules from all the security groups that are associated with the instance are evaluated. When you launch an instance in a virtual private cloud (VPC), you must either create a new security group or use one that already exists in that VPC. After you launch an instance, you can change its security groups.

When you **define a rule**, you can specify the allowable source of the network communication (inbound rules) or destination (outbound rules). The **source** can be an IP address, an IP address range, another security group, a gateway VPC endpoint, or anywhere (which means that all sources will be allowed). By default, a **security group** includes an **outbound rule** that allows all **outbound** traffic. You can remove the **rule** and add **outbound rules** that only allow specific **outbound** traffic. If your **security group** has no **outbound rules**, no **outbound** traffic that originates from your instance is allowed.

**In the example rule**, the rule allows Secure Shell (SSH) traffic over Transmission Control Protocol (TCP) port 22 if the source of the request is *My IP*. The *My IP* IP address is calculated by determining what IP address you are currently connected to the AWS Cloud from when you define the rule. 

**Identify or Create the Key Pair**

After you specify all the required configurations to launch an EC2 instance, and after you customize any optional EC2 launch wizard configuration settings, you are presented with a **Review Instance Launch** window. If you then choose **Launch**, a dialog asks you to choose an existing key pair, proceed without a key pair, or create a new key pair before you can choose **Launch Instances** and create the EC2 instance.

Amazon EC2 uses public–key cryptography to encrypt and decrypt login information. The technology uses a **public key** to encrypt a piece of data, and then the recipient uses the private key to decrypt the data. The public and private keys are known as a **key pair**. Public-key cryptography enables you to securely access your instances by using a private key instead of a password.

When you launch an instance, you specify a key pair. You can specify an existing key pair or a new key pair that you create at launch. If you create a new key pair, download it and save it in a safe location. This opportunity is the only chance you get to save the private key file. 

To connect *to* a **Windows** instance, use the private key to obtain the administrator password, and then log in to the EC2 instance's Windows Desktop by using Remote Desktop Protocol (RDP). To establish an SSH connection *from* a Windows machine to an Amazon EC2 instance, you can use a tool such as PuTTY, which will require the same private key.

**Amazon EC2 Instance Lifecycle**

An instance can be in one of the following states:

•**Pending** – When an instance is first launched from an AMI, or when you start a stopped instance, it enters the *pending* state when the instance is booted and deployed to a host computer. The instance type that you specified at launch determines the hardware of the host computer for your instance.

•**Running** – When the instance is fully booted and ready, it exits the *pending* state and enters the *running* state. You can connect over the internet to your running instance.

•**Rebooting** – AWS recommends you reboot an instance by using the Amazon EC2 console, AWS CLI, or AWS SDKs instead of invoking a reboot from within the guest operating system (OS). A rebooted instance stays on the same physical host, maintains the same public DNS name and public IP address, and if it has **instance store** volumes, it retains the data on those volumes.

•**Shutting down** – This state is an intermediary state between *running* and *terminated*.

•**Terminated** – A terminated instance remains visible in the Amazon EC2 console for a while before the virtual machine is deleted. However, you can’t connect to or recover a terminated instance.

•**Stopping** – Instances that are backed by Amazon EBS can be stopped. They enter the *stopping* state before they attain the fully *stopped* state.

**Stopped** – A *stopped* instance will not incur the same cost as a *running* instance. Starting a *stopped* instance puts it back into the *pending* state, which moves the instance to a new host machine. 

**Instance Hibernation Option**

Some instances that are backed by Amazon EBS support **hibernation.** When you hibernate an instance, the guest OS saves the contents from the instance memory (RAM) to your Amazon EBS root volume. When you restart the instance, the root volume is restored to its previous state, the RAM contents are reloaded, and the processes that were previously running on the instance are resumed. 

Only certain Linux AMIs that are backed by Amazon EBS and other certain instance types support hibernation. Hibernation also requires that you encrypt the root EBS volume. In addition, you must enable hibernation when the instance is first launched. You cannot enable hibernation on an existing instance that did not originally have hibernation enabled. 

**Consider using an Elastic IP address**

A **public IP address** is an IPv4 address that is reachable from the internet. Each instance that receives a public IP address is also given an external DNS hostname. For example, if the public IP address assigned to the instance is *203.0.113.25*, then the external DNS hostname might be *ec2-203-0-113-25.compute-1.amazonaws.com*. 

If you specify that a public IP address should be assigned to your instance, it is assigned from the AWS pool of public IPv4 addresses. The public IP address is not associated with your AWS account. When a public IP address is disassociated from your instance, it is released back into the public IPv4 address pool, and you will not be able to specify that you want to reuse it. AWS releases your instance's public IP address when the instance is stopped or terminated. Your stopped instance receives a new public IP address when it is restarted.

If you require a persistent public IP address, you might want to associate an **Elastic IP address** with the instance. To associate an Elastic IP address, you must first allocate a new Elastic IP address in the Region where the instance exists. After the Elastic IP address is allocated, you can associate the Elastic IP address with an EC2 instance.

By default, all AWS accounts are limited to five (5) Elastic IP addresses per Region because public (IPv4) internet addresses are a scarce public resource. However, this is a soft limit, and you can request a limit increase (which might be approved).

**EC2 Instance Metadata**

Instance metadata is data about your instance. You can view it while you are connected to the instance. To access it in a browser, go to the following URL: http://169.254.169.254/latest/meta-data/. The data can also be read programmatically, such as from a terminal window that has the cURL utility. In the terminal window, run **curl http://169.254.169.254/latest/meta-data/** to retrieve it. The IP address *169.254.169.254* is a link-local address and it is valid only from the instance.

Instance metadata provides much of the same information about the running instance that you can find in the AWS Management Console. For example, you can discover the public IP address, private IP address, public hostname, instance ID, security groups, Region, Availability Zone, and more.

Any user data that is specified at instance launch can also be accessed at the following URL: http://169.254.169.254/latest/**user-data**.

EC2 instance metadata can be used to configure or manage a running instance. For example, you can author a configuration script that accesses the metadata information and uses it to configure applications or OS settings.

**Amazon CloudWatch for monitoring**

You can monitor your instances by using Amazon CloudWatch, which collects and processes raw data from Amazon EC2 into readable, near-real-time metrics. These statistics are recorded for a period of 15 months, so you can access historical information and gain a better perspective on how your web application or service is performing.

By default, Amazon EC2 provides **basic monitoring**,** which sends metric data to CloudWatch in 5-minute periods. To send metric data for your instance to CloudWatch in 1-minute periods, you can enable **detailed monitoring** on the instance. For more information, see [Enable or Disable Detailed Monitoring for Your Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-cloudwatch-new.html).

The Amazon EC2 console displays a series of graphs based on the raw data from Amazon CloudWatch. Depending on your needs, you might prefer to get data for your instances from Amazon CloudWatch instead of through the graphs in the console. By default, Amazon CloudWatch does not provide RAM metrics for EC2 instances, though that is an option that you can configure if you want CloudWatch to collect that data.

**Section 3: Amazon EC2 Cost Optimization**             

**Amazon EC2 Pricing Models**

Amazon offers different pricing models to choose from when you want to run EC2 instances.

**Per second billing** is only available for On-Demand Instances, Reserved Instances, and Spot Instances that run Amazon Linux or Ubuntu.

**On-Demand Instances** are eligible for the[ ](https://aws.amazon.com/free/)[AWS Free Tier](https://aws.amazon.com/free/). They have the lowest upfront cost and the most flexibility. There are no upfront commitments or long-term contracts. It is a good choice for applications with short-term, spiky, or unpredictable workloads.

**Dedicated Hosts** are physical servers with instance capacity that is dedicated to your use. They enable you to use your existing per-socket, per-core, or per-VM software licenses, such as for Microsoft Windows or Microsoft SQL Server.

**Dedicated Instances** are instances that run in a virtual private cloud (VPC) on hardware that’s dedicated to a single customer. They are physically isolated at the host hardware level from instances that belong to other AWS accounts.

**Reserved Instance** enable you to reserve computing capacity for 1-year or 3-year term with lower hourly running costs. The discounted usage price is fixed for as long as you own the Reserved Instance. If you expect consistent, heavy use, they can provide substantial savings compared to On-Demand Instances.

**Scheduled Reserved Instances** enable you to purchase capacity reservations that recur on a daily, weekly, or monthly basis, with a specified duration, for a 1-year term. You pay for the time that the instances are scheduled, even if you do not use them.

**Spot Instances** enable you to bid on unused EC2 instances, which can lower your costs. The hourly price for a Spot Instance fluctuates depending on supply and demand. Your Spot Instance runs whenever your bid exceeds the current market price.

**Amazon EC2 Pricing Models: Benefits**

Each Amazon EC2 pricing model provides a different set of benefits.

**On-Demand Instances** offer the most flexibility, with no long-term contract and low rates.

**Spot Instances** provide large scale at a significantly discounted price.

**Reserved Instances** are a good choice if you have predictable or steady-state compute needs (for example, an instance that you know you want to keep running most or all of the time for months or years).

**Dedicated Hosts** are a good choice when you have licensing restrictions for the software you want to run on Amazon EC2, or when you have specific compliance or regulatory requirements that preclude you from using the other deployment options.

**Amazon EC2 Pricing Models: Use Cases**

**On-Demand Instance** pricing works well for spiky workloads or if you only need to test or run an application for a short time (for example, during application development or testing). Sometimes, your workloads are unpredictable, and On-Demand Instances are a good choice for these cases.

**Spot Instances** are a good choice if your applications can tolerate interruption with a 2-minute warning notification. By default, instances are terminated, but you can configure them to stop or hibernate instead. Common use cases include fault-tolerant applications such as web servers, API backends, and big data processing. Workloads that constantly save data to persistent storage (such as Amazon S3) are also good candidates.

**Reserved Instances** are a good choice when you have long-term workloads with predictable usage patterns, such as servers that you know you will want to run in a consistent way over many months.

**Dedicated Hosts** are a good choice when you have existing per-socket, per-core, or per-VM 

software licenses, or when you must address specific corporate compliance and regulatory requirements. 




**The Four Pillars of Cost Optimization**      

To optimize costs, you must consider four consistent, powerful drivers:

•**Right-size** – Choose the right balance of instance types. Notice when servers can be either sized down or turned off, and still meet your performance requirements.

•**Increase elasticity** – Design your deployments to reduce the amount of server capacity that is idle by implementing deployments that are elastic, such as deployments that use automatic scaling to handle peak loads.

•**Optimal pricing model** – Recognize the available pricing options. Analyze your usage patterns so that you can run EC2 instances with the right mix of pricing options.

•**Optimize storage choices** – Analyze the storage requirements of your deployments. Reduce unused storage overhead when possible, and choose less expensive storage options if they can still meet your requirements for storage performance.



**Pillar 1: Right Size**

First, consider right-sizing. AWS offers approximately 60 instance types and sizes. The wide choice of options enables customers to select the instance that best fits their workload. It can be difficult to know where to start and what instance choice will prove to be the best, from both a technical perspective and a cost perspective. **Right-sizing** is the process of reviewing deployed resources and looking for opportunities to downsize when possible. 

**To right-size:**

•**Select** the cheapest instance available that still meets your performance requirements.

•**Review** CPU, RAM, storage, and network utilization to identify instances that could be downsized. You might want to provision a variety of instance types and sizes in a test environment, and then test your application on those different test deployments to identify which instances offer the best performance-to-cost ratio. For right-sizing, use techniques such as load testing to your advantage.

•**Use** Amazon CloudWatch metrics and set up custom metrics. A metric represents a time-ordered set of values that are published to CloudWatch (for example, the CPU usage of a particular EC2 instance). Data points can come from any application or business activity for which you collect data. 




**Pillar 2: Increase Elasticity**

One form of **elasticity** is to create, start, or use EC2 instances when they are needed, but then to turn them off when they are not in use. Elasticity is one of the central tenets of the cloud, but customers often go through a learning process to operationalize elasticity to drive cost savings.



The easiest way for large customers to embrace elasticity is to look for resources that look like good candidates for stopping or hibernating, such as non-production environments, development workloads, or test workloads. For example, if you run development or test workloads in a single time zone, you can easily turn off those instances outside of business hours** and thus reduce runtime costs by perhaps 65 percent. The concept is similar to why there is a light switch next to the door, and why most offices encourage employees *to turn off the lights on their way out of the office each night.*

For production workloads, configuring more precise and granular automatic scaling policies can help you take advantage of horizontal scaling to meet peak capacity needs and to not pay for peak capacity all the time.



As a rule of thumb, *y*ou should target 20–30 percent of your Amazon EC2 instances to run as On-Demand Instances or Spot Instances, and you should also actively look for ways to maximize elasticity.

**Pillar 3: Optimal Pricing Model**

AWS provides a number of pricing models for Amazon EC2 to help customers save money. The models available were discussed in detail earlier in this module. Customers can combine multiple purchase types to optimize pricing based on their current and forecast capacity needs.

Customers are also encouraged to consider their application architecture. For example, does the functionality provided by your application need to run on an EC2 virtual machine? Perhaps by making use of the AWS Lambda service instead, you could significantly decrease your costs. 

**Pillar 4: Optimize Storage Choices**

Customers can also reduce storage costs. When you launch EC2 instances, different instance types offer different storage options. It is a best practice to try to reduce costs while also maintaining storage performance and availability.

One way you can accomplish this is by **resizing EBS volumes**. For example, if you originally provisioned a 500-GB volume for an EC2 instance that will only need a maximum of 20 GB of storage space, you can reduce the size of the volume and save on costs.

There are also a variety of **EBS volume types**. Choose the least expensive type that still meets your performance requirements. For example, Amazon EBS Throughput Optimized HDD (st1) storage typically costs half as much as the default General Purpose SSD (gp2) storage option. If an st1 drive will meet the needs of your workload, take advantage of the cost savings.

Customers often use **EBS** **snapshots** to create data backups. However, some customers forget to delete snapshots that are no longer needed. Delete these unneeded snapshots to save on costs.

Finally, try to identify the most **appropriate destination for specific types of data**. Does your application need the data it uses to reside on Amazon EBS? Would the application run equally as well if it used Amazon S3 for storage instead? Configuring data lifecycle policies can also reduce costs. For example, you might automate the migration of older infrequently accessed data to cheaper storage locations, such as Amazon Simple Storage Service Glacier.

**Measure, monitor, and improve**

If it is done correctly, cost optimization is not a one-time process that a customer completes. 

Instead, by routinely measuring and analyzing your systems, you can continually improve and adjust your costs.

**Tagging** helps provide information about *what resources* are being used *by whom* and *for what purpose*. You can activate cost allocation tags in the Billing and Cost Management console, and AWS can generate a cost allocation report with usage and costs grouped by your active tags. Apply tags that represent business categories (such as cost centers, application names, or owners) to organize your costs across multiple services.

**Encourage teams to architect for cost**. AWS Cost Explorer is a free tool that you can use to view graphs of your costs. You can use Cost Explorer to see patterns in how much you spend on AWS resources over time, identify areas that need further inquiry, and see trends that you can use to understand your costs.

Use AWS services such as **AWS Trusted Advisor**, which** provides real-time guidance to help you provision resources that follow AWS best practices.

Cost-optimization efforts are typically more successful when the responsibility for cost optimization is assigned to an individual or to a team. 









**Section 4: Container Services**

**Container Basics**

**Containers** are a method of **operating system virtualization** that enables you to run an application and its dependencies in resource-isolated processes. By using containers, you can easily package an application's code, configurations, and dependencies into easy-to-use building blocks that deliver environmental consistency, operational efficiency, developer productivity, and version control. 

Containers are smaller than virtual machines, and do not contain an entire operating system. Instead, containers *share a virtualized operating system* and run as resource-isolated processes, which ensure quick, reliable, and consistent deployments. Containers hold everything that the software needs to run, such as libraries, system tools, code, and the runtime.

Containers deliver **environmental consistency** because the application’s code, configurations, and dependencies are packaged into a single object.

In terms of space, container images are usually an order of magnitude smaller than virtual machines. Spinning up a container happens in hundreds of milliseconds. Thus, by using containers, you can use a fast, portable, and infrastructure-agnostic execution environment.

Containers can help ensure that applications deploy quickly, reliably, and consistently, regardless of deployment environment. Containers also give you more granular control over resources, which gives your infrastructure improved efficiency. 

**What is Docker?**

Docker is installed on each server that will host containers, and it provides simple commands that you can use to build, start, or stop containers.

By using Docker, you can quickly deploy and scale applications into any environment.

Docker is best used as a solution when you want to:

•Standardize environments

•Reduce conflicts between language stacks and versions

•Use containers as a service

•Run microservices using standardized code deployments

•Require portability for data processing

**Containers vs Virtual Machines**

Many people who are first introduced to the concept of a container think that containers are exactly like virtual machines. However, the differences are in the details. One significant difference is that virtual machines run directly on a hypervisor, but containers can run on any Linux OS if they have the appropriate kernel feature support and the Docker daemon is present. This makes containers very portable. Your laptop, your VM, your EC2 instance, and your bare metal server are all potential hosts where you can run a container.

**Amazon Elastic Container Service (Amazon ECS)**

**Amazon Elastic Container Service (Amazon ECS)** is a highly scalable, high-performance container management service that supports Docker containers. Amazon ECS enables you to easily run applications on a managed cluster of Amazon EC2 instances.

Essential Amazon ECS features include the ability to:

•**Launch** up to tens of thousands of Docker containers in seconds

•**Monitor** container deployment

•**Manage** the state of the cluster that runs the containers

•**Schedule** containers by using a built-in scheduler or a third-party scheduler (for example, Apache Mesos or Blox)

Amazon ECS clusters can also use Spot Instances and Reserved Instances. 



**Amazon ECS Orchestrates Containers**

To prepare your application to run on Amazon ECS, you create a **task definition** which is a text file that **describes one or more containers**, up to a maximum of ten, that form your application. It can be thought of as a blueprint for your application. Task definitions specify parameters for your application, for example which containers to use, which ports should be opened for your application, and what data volumes should be used with the containers in the task.

A **task** is the instantiation of a task definition within a cluster. You can specify the number of tasks that will run on your cluster. The **Amazon ECS task scheduler** is responsible for placing tasks within your cluster. A task will run anywhere from one to ten containers, depending on the task definition you defined.

When Amazon ECS runs the containers that make up your task, it places them on an **ECS** **cluster**. The cluster (when you choose the EC2 launch type) consists of a group of EC2 instances each of which is running an **Amazon ECS container agent**. 

Amazon ECS provides multiple scheduling strategies that will place containers across your clusters based on your resource needs (for example, CPU or RAM) and availability requirements. 




**Amazon ECS Cluster Options**

When you create an Amazon ECS cluster, you have three options:

•A **Networking Only** cluster (powered by AWS Fargate)

•An **EC2 Linux + Networking** cluster

•An **EC2** **Windows** + **Networking** cluster

If you choose one of the two **EC2 launch type** options, you will then be prompted to choose whether the cluster EC2 instances will run as On-Demand Instances or Spot Instances. In addition, you will need to specify many details about the EC2 instances that will make up your cluster—the same details that you must specify when you launch a stand lone EC2 instance. In this way, the EC2 launch type provides more granular control over the infrastructure that runs your container applications because you manage the EC2 instances that make up the cluster.

Amazon ECS keeps track of all the CPU, memory, and other resources in your cluster. Amazon ECS also finds the best server for your container on based on your specified resource requirements.

If you choose the networking-only **Fargate** **launch type**, then the cluster that will run your containers will be managed by AWS. With this option, you only need to package your application in containers, specify the CPU and memory requirements, define networking and 

IAM policies, and launch the application. You do not need to provision, configure, or scale the cluster. It removes the need to choose server types, decide when to scale your clusters, or optimize cluster packing. The Fargate option enables you to focus on designing and building your applications.

**What is Kubernetes?**

**Kubernetes** is open source software for container orchestration. Kubernetes can work with many containerization technologies, including Docker. Because it is a popular open source project, a large community of developers and companies build extensions, integrations, and plugins that keep the software relevant, and new and in-demand features are added frequently.

Kubernetes enables you to deploy and manage **containerized applications** at scale. With Kubernetes, you can run any type of containerized application by using the same toolset in both on-premises data centers and the cloud. Kubernetes manages a **cluster** of compute instances (called **nodes**). It runs containers on the cluster, which are based on where compute resources are available and the resource requirements of each container. Containers** are run in logical groupings called **pods**. You can run and scale one or many containers together as a pod. Each pod is given an IP address and a single Domain Name System (DNS) name, which Kubernetes uses to connect your services with each other and external traffic.

A key advantage of Kubernetes is that you can use it to run your containerized applications anywhere without needing to change your operational tooling. For example, applications can be moved from local on-premises development machines to production deployments in the cloud by using the same operational tooling. 

**Amazon Elastic Kubernetes Service (Amazon EKS)**

You might think that you could launch one or more Amazon EC2 instances, install Docker on each instance, install Kubernetes on the cluster, and manage and run Kubernetes yourself. While that is an option, AWS provides a service called Amazon Elastic Kubernetes Service (Amazon EKS) that simplifies the management of Kubernetes clusters.

**Amazon Elastic Kubernetes Service (Amazon EKS**) is a managed Kubernetes service that makes it easy for you to run Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane. It is certified Kubernetes conformant, so existing applications that run on upstream Kubernetes are compatible with Amazon EKS.

Amazon EKS automatically manages the availability and scalability of the cluster nodes that are responsible for starting and stopping containers, scheduling containers on virtual machines, storing cluster data, and other tasks. It automatically detects and replaces unhealthy control plane nodes for each cluster. You can take advantage of the performance, scale, reliability, and availability of the AWS Cloud, which includes AWS networking and security services like Application Load Balancers for load distribution, IAM for role-based access control, and VPC for pod networking.

You may be wondering why Amazon offers both Amazon ECS and Amazon EKS, since they are both capable of orchestrating Docker containers. The reason that both services exist is to provide customers with flexible options. You can decide which option best matches your needs. 

**Amazon Elastic Container Registry (Amazon ECR)**

**Amazon Elastic Container Registry (Amazon ECR)** is a fully managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. It is **integrated with Amazon ECS**, so you can store, run, and manage container images for applications that run on Amazon ECS. Specify the Amazon ECR repository in your task definition, and Amazon ECS will retrieve the appropriate images for your applications.

Amazon ECR supports Docker Registry HTTP API version 2, which enables you to interact with 

Amazon ECR by using Docker CLI commands or your preferred Docker tools. Thus, you can maintain your existing development workflow and access Amazon ECR from any Docker environment—whether it is in the cloud, on premises, or on your local machine.

You can transfer your container images to and from Amazon ECS via HTTPS. Your images are also automatically *encrypted* at rest using Amazon S3 server-side encryption.

It is also possible to use Amazon ECR images with **Amazon EKS**. See the[ ](https://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_on_EKS.html)[Using Amazon ECR Images with Amazon EKS](https://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_on_EKS.html) documentation for details.

**Section 5: Introduction to AWS Lambda**

**AWS Lambda: Run code without servers**

As you saw in the earlier sections of this module, AWS offers many compute options. For example, **Amazon EC2** provides virtual machines. As another example, **Amazon ECS** and **Amazon EKS** are container-based compute services.

However, there is another approach to compute that does not require you to provision or manage servers. This third approach is often referred to as **serverless computing**.

**AWS Lambda** is an event-driven, serverless compute service. Lambda enables you to run code without provisioning or managing servers.

You create a **Lambda function**, which is the AWS resource that contains the code that you 

upload. You then set the Lambda function to be triggered, either on a scheduled basis or in response to an event. Your code only runs when it is triggered.

You **pay only for the compute time you consume**—you are not charged when your code is not running.

**Benefits of Lambda**

With Lambda, there are no new languages, tools, or frameworks to learn. Lambda **supports multiple programming languages**, including Java, Go, PowerShell, Node.js, C#, Python, and Ruby. Your code can use any library, either native or third-party.

Lambda **completely automates the administration**. It manages all the infrastructure to run your code on highly available, fault-tolerant infrastructure, which enables you to focus on building differentiated backend services. Lambda seamlessly deploys your code; does all the administration, maintenance, and security patches; and provides built-in logging and monitoring through Amazon CloudWatch.

Lambda provides **built-in fault tolerance**. It maintains compute capacity across multiple Availability Zones in each Region to help protect your code against individual machine failures or data center failures. There are no maintenance windows or scheduled downtimes.

You can **orchestrate multiple Lambda functions** for complex or long-running tasks by building workflows with AWS Step Functions. Use Step Functions to define workflows. These workflows trigger a collection of Lambda functions by using sequential, parallel, branching, and error-handling steps. With Step Functions and Lambda, you can build stateful, long-running processes for applications and backends.

With Lambda, you **pay only for the requests that are served and the compute time that is required to run your code**. Billing is metered in increments of 100 milliseconds, which make it cost-effective and easy to scale automatically from a few requests per day to thousands of requests per second.

**AWS Lambda Event Sources**

An **event source** is an AWS service or a developer-created application that produces events that trigger an AWS Lambda function to run.

Some services publish events to Lambda by invoking the Lambda function directly. These services that invoke Lambda functions **asynchronously** include, but are not limited to, Amazon S3, Amazon Simple Notification Service (Amazon SNS), and Amazon CloudWatch Events.

Lambda can also poll resources in other services that do not publish events to Lambda. For example, Lambda can pull records from an **Amazon Simple Queue Service (Amazon SQS)** queue and execute a Lambda function for each fetched message. Lambda can similarly read events from **Amazon DynamoDB**.

Some services, such as Elastic Load Balancing (Application Load Balancer) and Amazon API Gateway can **invoke your Lambda function directly**.

You can invoke Lambda functions directly with the Lambda console, the Lambda API, the AWS software development kit (SDK), the AWS CLI, and AWS toolkits. The direct invocation approach can be useful, such as when you are developing a mobile app and want the app to call Lambda functions. See the[ ](https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html)[Using Lambda with Other Services](https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html) documentation for further details about all supported services.

**AWS Lambda automatically monitors Lambda functions by using Amazon CloudWatch**. To help you troubleshoot failures in a function, Lambda logs all requests that are handled by your function. It also **automatically stores logs that are generated by your code** through Amazon CloudWatch Logs. 



**AWS Lambda Function Configuration**

Remember that a Lambda function is the custom code that you write to process events, and that Lambda executes the Lambda function on your behalf.

When you use the AWS Management Console to create a **Lambda function**,** you first give the function a name. Then, you specify:

•The **runtime environment** the function will use (for example, a version of Python or Node.js)

•An **execution role** (to grant IAM permission to the function so that it can interact with other AWS services as necessary)

Next, after you click **Create Function**, you configure the function. Configurations include:

•Add a **trigger** (specify one of the available **event sources** from the previous slide)

•Add your **function code** (use the provided code editor or upload a file that contains your code)

•Specify the **memory** in MB to allocate to your function (128 MB to 3,008 MB)

•Optionally specify environment variables, description, timeout, the specific virtual private cloud (VPC) to run the function in, tags you would like to use, and other settings. Full details are in the[ ](https://docs.aws.amazon.com/lambda/latest/dg/resource-model.html)[**AWS Lambda Function Configuration**](https://docs.aws.amazon.com/lambda/latest/dg/resource-model.html) documentation.


All of the above settings end up in a **Lambda deployment package** which is a ZIP archive that contains your function code and dependencies. When you use the Lambda console to author your function, the console manages the package for you. However, you need to create a deployment package if you use the Lambda API to manage functions.

**AWS Lambda Limits**

AWS Lambda does have some limits that you know about when you create and deploy Lambda functions.

AWS Lambda limits the amount of compute and storage resources that you can use to run and store functions. For example, as of this writing, the maximum memory allocation for a single Lambda function is 3,008 MB. It also has limits of 1,000 concurrent executions in a Region. Lambda functions can be configured to run up to 15 minutes per execution. You can set the timeout to any value between 1 second and 15 minutes. If you are troubleshooting a Lambda deployment, keep these limits in mind.

There are limits on the **deployment package size** of a function (250 MB). A **layer** is a ZIP archive that contains libraries, a custom runtime, or other dependencies. With layers, you can use libraries in your function without needing to include them in your **deployment package**. Using layers can help avoid reaching the size limit for deployment package. Layers are also a good way to share code and data between Lambda functions.

Limits are either soft or hard. **Soft limits** on an account can potentially be relaxed by submitting a support ticket and providing justification for the request. **Hard limits** cannot be increased.

For the details on current AWS Lambda limits, refer to the[ ](https://docs.aws.amazon.com/lambda/latest/dg/limits.html)[AWS Lambda Limits](https://docs.aws.amazon.com/lambda/latest/dg/limits.html) documentation.







**Section 6: Introduction to AWS Beanstalk**

**AWS Elastic Beanstalk**

AWS Elastic Beanstalk is another AWS compute service option. It is a platform as a service (or PaaS) that facilitates the quick deployment, scaling, and management of your web applications and services.

You remain in control. The entire platform is already built, and you only need to upload your code. Choose your instance type, your database, set and adjust automatic scaling, update your application, access the server log files, and enable HTTPS on the load balancer.

You upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning and load balancing to automatic scaling and monitoring application health. At the same time, you retain full control over the AWS resources that power your application, and you can access the underlying resources at any time.

There is no additional charge for AWS Elastic Beanstalk. You pay for the AWS resources (for example, EC2 instances or S3 buckets) you create to store and run your application. You only pay for what you use, as you use it. There are no minimum fees and no upfront commitments.

**AWS Elastic Beanstalk Deployments**    

AWS Elastic Beanstalk enables you to deploy your code through the AWS Management Console, the AWS Command Line Interface (AWS CLI), Visual Studio, and Eclipse. It provides all the application services that you need for your application. The only thing you must create is your code. Elastic Beanstalk is designed to make deploying your application a quick and easy process.

Elastic Beanstalk supports a broad range of platforms. Supported platforms include Docker, Go, Java, .NET, Node.js, PHP, Python, and Ruby.

AWS Elastic Beanstalk deploys your code on **Apache Tomcat** for Java applications; **Apache HTTP Server** for PHP and Python applications; **NGINX** or **Apache HTTP Server** for Node.js applications; **Passenger** or **Puma** for Ruby applications; and **Microsoft Internet Information Services (IIS)** for .NET applications, Java SE, Docker, and Go.

**Benefits of Elastic Beanstalk**

Elastic Beanstalk is **fast and simple to start** **using**. Use the AWS Management Console, a Git repository, or an integrated development environment (IDE) such as Eclipse or Visual Studio to upload your application. Elastic Beanstalk automatically handles the deployment details of capacity provisioning, load balancing, automatic scaling, and monitoring application health.



You can improve your **developer productivity** by focusing on writing code instead of managing and configuring servers, databases, load balancers, firewalls, and networks. AWS updates the underlying platform that runs your application with patches and updates.



Elastic Beanstalk is **difficult to outgrow**. With Elastic Beanstalk, your application can handle peaks in workload or traffic while minimizing your costs. It automatically scales your application up or down based on your application's specific needs by using easily adjustable automatic scaling settings. You can use CPU utilization metrics to trigger automatic scaling actions.

You have the **freedom to select the AWS resources**—such as Amazon EC2 instance type—that are optimal for your application. Elastic Beanstalk enables you to retain full control over the AWS resources that power your application. If you decide that you want to take over some (or all) of the elements of your infrastructure, you can do so seamlessly by using the management capabilities that are provided by Elastic Beanstalk.

**Module 7: Storage**

**Core AWS Services**

Storage is another AWS core service category. Some broad categories of storage include: instance store (ephemeral storage), Amazon EBS, Amazon EFS, Amazon S3, and Amazon S3 Glacier.

•Instance store, or *ephemeral storage*, is **temporary storage** that is added to your Amazon EC2 instance.

•Amazon EBS is **persistent**, **mountable storage** that can be mounted as a device to an Amazon EC2 instance. Amazon EBS can be mounted to an Amazon EC2 instance only within the same Availability Zone. Only one Amazon EC2 instance at a time can mount an Amazon EBS volume.

•Amazon EFS is a shared file system that multiple Amazon EC2 instances can mount at the same time.

•Amazon S3 is persistent storage where each file becomes an object and is available through a Uniform Resource Locator (URL); it can be accessed from anywhere.

•Amazon S3 Glacier is for cold storage for data that is not accessed frequently (for example, when you need long-term data storage for archival or compliance reasons). 






**Section 1: Amazon Elastic Block Store (Amazon EBS)**

**Storage**  

Amazon EBS provides persistent block storage volumes for use with Amazon EC2 instances. Persistent storage is any data storage device that retains data after power to that device is shut off. It is also sometimes called **non-volatile storage**.

Each Amazon EBS volume is automatically replicated *within* its Availability Zone to protect you from component failure. It is designed for high availability and durability. Amazon EBS volumes provide the consistent and low-latency performance that is needed to run your workloads.

With Amazon EBS, you can scale your usage up or down within minutes, while paying a low price for only what you provision.

**AWS Storage Options: Block Storage vs Object Storage**

What happens if you want to change one character in a 1-GB file? With block storage, you change only the block that contains the character. With object storage, the entire file must be updated.



One critical difference between some storage types is whether they offer *block-level storage* or *object-level storage*.



This difference has a major effect on the throughput, latency, and cost of your storage solution. Block storage solutions are typically faster and use less bandwidth, but they can cost more than object-level storage.

**Amazon EBS**

Amazon EBS enables you to create individual storage volumes and attach them to an Amazon EC2 instance. Amazon EBS offers block-level storage, where its volumes are automatically replicated within its Availability Zone. Amazon EBS is designed to provide durable, detachable, block-level storage (which is like an external hard drive) for your Amazon EC2 instances. Because they are directly attached to the instances, they can provide low latency between where the data is stored and where it might be used on the instance.



For this reason, they can be used to run a database with an Amazon EC2 instance. Amazon EBS volumes are included as part of the backup of your instances into Amazon Machine Images (or AMIs). AMIs are stored in Amazon S3 and can be reused to create new Amazon EC2 instances later.

A backup of an Amazon EBS volume is called a *snapshot*. The first snapshot is called the *baseline snapshot*. Any other snapshot after the baseline captures only what is different from the previous snapshot.



Amazon EBS volumes uses include:

•Boot volumes and storage for Amazon EC2 instances

•Data storage with a file system

•Database hosts

•Enterprise applications

**Amazon EBS Volume Types**

Matching the correct technology to your workload is a best practice for reducing storage costs. Provisioned IOPS SSD-backed Amazon EBS volumes can give you the highest performance. However, if your application doesn't require or won't use performance that high, General Purpose SSD is usually sufficient. Only SSDs can be used as boot volumes for EC2 instances. The lower-cost options might be a solution for additional storage or use cases other than boot volumes. 

**Amazon EBS volume type use cases**

As mentioned previously an **Amazon EBS volume** is a durable, block-level storage device that you can attach to a single EC2 instance. You can use Amazon EBS volumes as primary storage for data that requires frequent updates, such as the system drive for an instance or storage for a database application. You can also use them for throughput-intensive applications that perform continuous disk scans. Amazon EBS volumes persist independently from the running life of an EC2 instance.

Use cases for EBS vary by the storage type used and whether you are using General Purpose of Provisioned IOPS.

**Amazon EBS Features**

To provide an even higher level of data durability, Amazon EBS enables you to create **point-in-time snapshots** of your volumes, and you can re-create a new volume from a snapshot at any time. You can also share snapshots or even copy snapshots to different AWS Regions for even greater **disaster recovery (DR) protection**. For example, you can encrypt and share your snapshots from Virginia in the US to Tokyo, Japan.

You can also have encrypted Amazon EBS volumes at no additional cost, so the data that moves between the EC2 instance and the EBS volume inside AWS data centers is encrypted in transit.



As your company grows, the amount of data that is stored on your Amazon EBS volumes is also likely to grow. Amazon EBS volumes can increase capacity and change to different types, so you can change from hard disk drives (HDDs) to solid state drives (SSDs) or increase from a 50-GB volume to a 16-TB volume. For example, you can do this resize operation dynamically without needing to stop the instances. 

**Amazon EBS: Volumes, OPS, and Pricing**

When you begin to estimate the cost for Amazon EBS, you must consider the following:

1\.**Volumes –** Volume storage for all Amazon EBS volume types is charged by the amount you provision in GB per month, until you release the storage.

2\.**IOPS –** I/O is included in the price of General Purpose SSD volumes. However, for Amazon EBS magnetic volumes, I/O is charged by the number of requests that you make to your volume. With Provisioned IOPS SSD volumes, you are also charged by the amount you provision in IOPS (multiplied by the percentage of days that you provision for the month).

The pricing and provisioning of Amazon EBS are complex. In general, you pay for the size of the volume and its usage.

**Amazon EBS: Snapshots and Data Transfer**

3\.**Snapshots –** Amazon EBS enables you to back up snapshots of your data to Amazon S3 for durable recovery. If you opt for Amazon EBS snapshots, the added cost is per GB-month of data stored.

4\.**Data transfer –** When you copy Amazon EBS snapshots, you are charged for the data that is transferred across Regions. After the snapshot is copied, standard Amazon EBS snapshot charges apply for storage in the destination Region.

**Section 4: Amazon Simple Storage Service (Amazon S3)**

**Storage**

Amazon S3 is object-level storage, which means that if you want to change a part of a file, you must make the change and then re-upload the entire modified file. Amazon S3 stores data as objects within resources that are called **buckets.**

**AWS S3 Overview**

Amazon S3 is a managed cloud storage solution that is designed to scale seamlessly and provide 11 9s of durability. You can store virtually as many objects as you want in a bucket, and you can write, read, and delete objects in your bucket. Bucket names are universal and must be unique across all existing bucket names in Amazon S3. Objects can be up to 5 TB in size. By default, data in Amazon S3 is stored redundantly across multiple facilities and multiple devices in each facility.

The data that you store in Amazon S3 is not associated with any particular server, and you do not need manage any infrastructure yourself. You can put as many objects into Amazon S3 as you want. Amazon S3 holds trillions of objects and regularly peaks at millions of requests per second.

Objects can be almost any data file, such as images, videos, or server logs. Because Amazon S3 supports objects as large as several terabytes in size, you can even store database snapshots as objects. Amazon S3 also provides low-latency access to the data over the internet by Hypertext Transfer Protocol (HTTP) or Secure HTTP (HTTPS), so you can retrieve data anytime from anywhere. You can also access Amazon S3 privately through a virtual private cloud (VPC) endpoint. You get fine-grained control over who can access your data by using AWS Identity and Access Management (IAM) policies, Amazon S3 bucket policies, and even per-object access control lists.

By default, none of your data is shared publicly. You can also encrypt your data in transit and choose to enable server-side encryption on your objects.

You can access Amazon S3 through the web-based AWS Management Console; programmatically through the API and SDKs; or with third-party solutions, which use the API or the SDKs.

Amazon S3 includes event notifications that enable you to set up automatic notifications when certain events occur, such as when an object is uploaded to a bucket or deleted from a specific bucket. Those notifications can be sent to you, or they can be used to trigger other processes, such as AWS Lambda functions.

With storage class analysis, you can analyze storage access patterns and transition the right data to the right storage class. The Amazon S3 Analytics feature automatically identifies the optimal lifecycle policy to transition less frequently accessed storage to Amazon S3 Standard – Infrequent Access (Amazon S3 Standard-IA). You can configure a storage class analysis policy to monitor an entire bucket, a prefix, or an object tag.

When an infrequent access pattern is observed, you can easily create a new lifecycle age policy that is based on the results. Storage class analysis also provides daily visualizations of your storage usage in the AWS Management Console. You can export them to an Amazon S3 bucket to analyze by using the business intelligence (BI) tools of your choice, such as Amazon QuickSight.








**Amazon S3 Storage Classes**

Amazon S3 offers a range of object-level storage classes that are designed for different use cases. These classes include:

•**Amazon S3 Standard** – Amazon S3 Standard is designed for high durability, availability, and performance object storage for frequently accessed data. Because it delivers low latency and high throughput, Amazon S3 Standard is appropriate for a variety of use cases, including cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics.

•**Amazon S3 Intelligent-Tiering** – The Amazon S3 Intelligent-Tiering storage class is designed to optimize costs by automatically moving data to the most cost-effective access tier, without performance impact or operational overhead. For a small monthly monitoring and automation fee per object, Amazon S3 monitors access patterns of the objects in Amazon S3 Intelligent-Tiering, and moves the objects that have not been accessed for 30 consecutive days to the infrequent access tier. If an object in the infrequent access tier is accessed, it is automatically moved back to the frequent access tier. There are no retrieval fees when you use the Amazon S3 Intelligent-Tiering storage class, and no additional fees when objects are moved between access tiers. It works well for long-lived data with access patterns that are unknown or unpredictable.

•**Amazon S3 Standard-Infrequent Access (Amazon S3 Standard-IA)** – The Amazon S3 Standard-IA storage class is used for data that is accessed less frequently, but requires rapid access when needed. Amazon S3 Standard-IA is designed to provide the high durability, high throughput, and low latency of Amazon S3 Standard, with a low per-GB storage price and per-GB retrieval fee. This combination of low cost and high performance makes Amazon S3 Standard-IA good for long-term storage and backups, and as a data store for disaster recovery files.

•**Amazon S3 One Zone-Infrequent Access (Amazon S3 One Zone-IA)** – Amazon S3 One Zone-IA is for data that is accessed less frequently, but requires rapid access when needed. Unlike other Amazon S3 storage classes, which store data in a minimum of three Availability Zones, Amazon S3 One Zone-IA stores data in a single Availability Zone and it costs less than Amazon S3 Standard-IA. Amazon S3 One Zone-IA works well for customers who want a lower-cost option for infrequently accessed data, but do not require the availability and resilience of Amazon S3 Standard or Amazon S3 Standard-IA. It is a good choice for storing secondary backup copies of on-premises data or easily recreatable data. You can also use it as cost-effective storage for data that is replicated from another AWS Region by using Amazon S3 Cross-Region Replication.

•**Amazon S3 Glacier** – Amazon S3 Glacier is a secure, durable, and low-cost storage class for data archiving. You can reliably store any amount of data at costs that are competitive with—or cheaper than—on-premises solutions. To keep costs low yet suitable for varying needs, Amazon S3 Glacier provides three retrieval options that range from a few minutes to hours. You can upload objects directly to Amazon S3 Glacier, or use Amazon S3 lifecycle policies to transfer data between any of the Amazon S3 storage classes for active data (Amazon S3 Standard, Amazon S3 Intelligent-Tiering, Amazon S3 Standard-IA, and Amazon S3 One Zone-IA) and Amazon S3 Glacier.

•**Amazon S3 Glacier Deep Archive** – Amazon S3 Glacier Deep Archive is the lowest-cost storage class for Amazon S3. It supports long-term retention and digital preservation for data that might be accessed once or twice in a year. It is designed for customers — particularly customers in highly regulated industries, such as financial services, healthcare, and public sectors — that retain datasets for 7–10 years (or more) to meet regulatory compliance requirements. Amazon S3 Glacier Deep Archive can also be used for backup and disaster recovery use cases. It is a cost-effective and easy-to-manage alternative to magnetic tape systems, whether these tape systems are on-premises libraries or off-premises services. Amazon S3 Glacier Deep Archive complements Amazon S3 Glacier, and it is also designed to provide 11 9s of durability. All objects that are stored in Amazon S3 Glacier Deep Archive are replicated and stored across at least three geographically dispersed Availability Zones, and these objects can be restored within 12 hours.

**Amazon S3 Bucket URLs (two styles)**

To use Amazon S3 effectively, you must understand a few simple concepts. First, Amazon S3 stores data inside **buckets**. Buckets are essentially the prefix for a set of files, and must be uniquely named across all of Amazon S3 globally. Buckets are logical containers for objects. You can have one or more buckets in your account. You can control access for each bucket—who can create, delete, and list objects in the bucket. You can also view access logs for the bucket and its objects, and choose the geographical region where Amazon S3 stores the bucket and its contents.



To upload your data (such as photos, videos, or documents), create a bucket in an AWS Region, and then upload almost any number of objects to the bucket.



In the example, Amazon S3 was used to create a bucket in the Tokyo Region, which is identified within AWS formally by its Region code: *ap-northeast-1*



The URL for a bucket is structured like the examples. You can use two different URL styles to refer to buckets.

Amazon S3 refers to files as *objects*. As soon as you have a bucket, you can store almost any number of objects inside it. An object is composed of data and any metadata that describes that file, including a URL. To store an object in Amazon S3, you upload the file that you want to store to a bucket.

When you upload a file, you can set permissions on the data and any metadata. 

[***https://](https://s3/)***s3.ap-northeast-1.amazonaws.com/bucket-name***

[***https://](https://s3/) ***bucket-name.s3-ap-northeast-1.amazonaws.com***

**Amazon S3 Common Scenarios**

**Backup and storage –** Provide data backup and storage services for others

**Application hosting –** Provide services that deploy, install, and manage web applications

**Media hosting –** Build a redundant, scalable, and highly available infrastructure that hosts video, photo, or music uploads and downloads

**Software delivery –** Host your software applications that customers can download

**Amazon S3 Pricing**

With Amazon S3, specific costs vary depending on the Region and the specific requests that were made. You pay only for what you use, including gigabytes per month; transfer out of other Regions; and PUT, COPY, POST, LIST, and GET requests.

As a general rule, you pay only for transfers that cross the boundary of your Region, which means you do not pay for transfers **into** Amazon S3 or transfers out from Amazon S3 to Amazon CloudFront edge locations within that same Region.

**Amazon S3: Storage Pricing**

When you begin to estimate the costs of Amazon S3, you must consider the following:

1\.**Storage class type –**

•**Standard storage** is designed to provide 11 9s of durability and four 9s of availability.

•**S3 Standard – Infrequent Access (S-IA)** is a storage option within Amazon S3 that you can use to reduce your costs by storing less frequently accessed data at slightly lower levels of redundancy than Amazon S3 standard storage. Standard – Infrequent Access is designed to provide the same 11 9s of durability as Amazon S3, with three 9s of availability in a given year. Each class has different rates.

2\.**Amount of storage –** The number and size of objects stored in your Amazon S3 buckets.

3\.**Requests –** Consider the number and type of requests. GET requests incur charges at different rates than other requests, such as PUT and COPY requests.

•**GET –** Retrieves an object from Amazon S3. You must have READ access to use this operation.

•**PUT –** Adds an object to a bucket. You must have WRITE permissions on a bucket to add an object to it.

•**COPY –** Creates a copy of an object that is already stored in Amazon S3. A COPY operation is the same as performing a GET and then a PUT.

4\.**Data transfer –** Consider the amount of data that is transferred out of the Amazon S3 Region. Remember that data transfer in is free, but there is a charge for data transfer out.

**Section 3: Amazon Elastic File System (Amazon EFS)**

**Storage**

**Amazon Elastic File System (Amazon EFS)** provides simple, scalable, elastic file storage for use with AWS services and on-premises resources. It offers a simple interface that enables you to create and configure file systems quickly and easily. 

Amazon EFS is built to dynamically scale on demand without disrupting applications—it will grow and shrink automatically as you add and remove files. It is designed so that your applications have the storage they need, when they need it.

**Amazon EFS Features**

Amazon EFS is a fully managed service that makes it easy to set up and scale file storage in the AWS Cloud. You can use Amazon EFS to build a file system for big data and analytics, media processing workflows, content management, web serving, and home directories.

You can create file systems that are accessible to Amazon EC2 instances through a file system interface (using standard operating system file I/O APIs). These file systems support full file system access semantics, such as strong consistency and file locking.

Amazon EFS file systems can automatically scale from gigabytes to petabytes of data without the need to provision storage. Thousands of Amazon EC2 instances can access an Amazon EFS file system at the same time, and Amazon EFS is designed to provide consistent performance to each Amazon EC2 instance. Amazon EFS is also designed to be highly durable and highly available. Amazon EFS requires no minimum fee or setup costs, and you pay only for the storage that you use.


**Amazon EFS Architecture**

Amazon EFS provides file storage in the cloud. With Amazon EFS, you can create a file system, mount the file system on an Amazon EC2 instance, and then read and write data from to and from your file system. You can mount an Amazon EFS file system in your VPC, through NFS versions 4.0 and 4.1 (NFSv4).

You can access your Amazon EFS file system concurrently from Amazon EC2 instances in your VPC, so applications that scale beyond a single connection can access a file system. Amazon EC2 instances that run in multiple Availability Zones within the same AWS Region can access the file system, so many users can access and share a common data source. 

**Amazon EFS Implementation**

You must complete five steps to create and use your first Amazon EFS file system, mount it on an Amazon EC2 instance in your VPC, and test the end-to-end setup:

1\.Create your Amazon EC2 resources and launch your instance. (Before you can launch and connect to an Amazon EC2 instance, you must create a key pair, unless you already have one.)

2\.Create your Amazon EFS file system.

3\.In the appropriate subnets, create your mount targets.

4\.Next, connect to your Amazon EC2 instance and mount the Amazon EFS file system.

5\.Finally, clean up your resources and protect your AWS account.

**Amazon EFS Resources**

In Amazon EFS, a file system is the primary resource. Each file system has properties such as:

•ID

•Creation token

•Creation time

•File system size in bytes

•Number of mount targets that are created for the file system

•File system state

Amazon EFS also supports other resources to configure the primary resource. These resources include mount targets and tags.



**Mount target**: To access your file system, you must create mount targets in your VPC.

Each mount target has the following properties:

•The mount target ID

•The subnet ID for the subnet where it was created

•The file system ID for the file system where it was created

•An IP address where the file system can be mounted

•The mount target state

You can use the IP address or the Domain Name System (DNS) name in your mount command.

**Tags**: To help organize your file systems, you can assign your own metadata to each of the file systems that you create. Each tag is a key-value pair.

Think of mount targets and tags as subresources that do not exist unless they are associated with a file system.

**Section 4: Amazon S3 Glacier**

**Amazon S3 Glacier Review**

When you use Amazon S3 Glacier to archive data, you can store your data at an extremely low cost (even in comparison to Amazon S3), but you cannot retrieve your data immediately when you want it.

Data that is stored in Amazon S3 Glacier can take several hours to retrieve, which is why it works well for archiving.

There are three key Amazon S3 Glacier terms you should be familiar with:

•**Archive** – Any object (such as a photo, video, file, or document) that you store in Amazon S3 Glacier. It is the base unit of storage in Amazon S3 Glacier. Each archive has its own unique ID and it can also have a description.

•**Vault** – A container for storing archives. When you create a vault, you specify the vault name and the Region where you want to locate the vault.

•**Vault access policy** – Determine who can and cannot access the data that is stored in the vault, and what operations users can and cannot perform. One vault access permissions policy can be created for each vault to manage access permissions for that vault. You can also use a vault lock policy to make sure that a vault cannot be altered. Each vault can have one vault access policy and one vault lock policy that are attached to it.

You have three options for retrieving data, each with varying access times and cost:

•**Expedited** retrievals are typically made available within 1–5 minutes (highest cost).

•**Standard** retrievals typically complete within 3–5 hours (less time than expedited, more time than bulk).

•**Bulk** retrievals typically complete within 5–12 hours (lowest cost).

You might compare these options to choosing the cost for shipping a package by using the most economical method for your needs.


**Amazon S3 Glacier Use Cases**

**Media asset archiving**

Media assets—such as video and news footage—require durable storage and can grow to many petabytes over time. Amazon S3 Glacier enables you to archive older media content affordably and then move it to Amazon S3 for distribution when it is needed.

**Healthcare information archiving**

To meet regulatory requirements, hospital systems must retain petabytes of patient records—such as Low-Income Subsidy (LIS) information, picture archiving and communication system (PACS) data, or Electronic Health Records (EHR)—for decades. Amazon S3 Glacier can help you reliably archive patient record data securely at a very low cost.

**Regulatory and compliance archiving**

Many enterprises, like those in financial services and healthcare, must retain regulatory and compliance archives for extended durations. Amazon S3 Glacier Vault Lock can help you set compliance controls so you can work towards meeting your compliance objectives, such as the U.S. Securities and Exchange Commission (SEC) Rule 17a-4(f).

**Scientific data archiving**

Research organizations generate, analyze, and archive large amounts of data. By using Amazon S3 Glacier, you can reduce the complexities of hardware and facility management and capacity planning.

**Digital preservation**

Libraries and government agencies must handle data integrity challenges in their digital preservation efforts. Unlike traditional systems—which can require laborious data verification and manual repair—Amazon S3 Glacier performs regular, systematic data integrity checks, and it is designed to be automatically self-healing.

**Magnetic tape replacement**

On-premises or offsite tape libraries can lower storage costs, but they can require large upfront investments and specialized maintenance. Amazon S3 Glacier has no upfront cost and reduces the cost and burden of maintenance.

**Using Amazon S3 Glacier**

To store and access data in Amazon S3 Glacier, you can use the AWS Management Console. However, only a few operations—such as creating and deleting vaults, and creating and managing archive policies—are available in the console.

For almost all other operations and interactions with Amazon S3 Glacier, you must use either the Amazon S3 Glacier REST APIs, the AWS Java or .NET SDKs, or the AWS CLI.

You can also use lifecycle policies to archive data into Amazon S3 Glacier. 


**Lifecycle Policies**

You should automate the lifecycle of the data that you store in Amazon S3. By using lifecycle policies, you can cycle data at regular intervals between different Amazon S3 storage types. This automation reduces your overall cost, because you pay less for data as it becomes less important with time.

In addition to setting lifecycle rules per object, you can also set lifecycle rules per bucket.

Consider an example of a lifecycle policy that moves data as it ages from **Amazon S3 Standard** to **Amazon S3 Standard – Infrequent Access**, and finally, into **Amazon S3 Glacier** before it is deleted. Suppose that a user uploads a video to your application and your application generates a thumbnail preview of the video. This video preview is stored to Amazon S3 Standard, because it is likely that the user wants to access it right away.

Your usage data indicates that most thumbnail previews are not accessed after 30 days. Your lifecycle policy takes these previews and moves them to Amazon S3 – Infrequent Access after 30 days. After another 30 days elapse, the preview is unlikely to be accessed again. The preview is then moved to Amazon S3 Glacier, where it remains for 1 year. After 1 year, the preview is deleted. The important thing is that the lifecycle policy manages all this movement automatically.

**Storage Comparison**

While **Amazon S3** and **Amazon S3 Glacier** are both object storage solutions that enable you to store a virtually unlimited amount of data, they have some critical differences between them. 

The chart outlines some of these differences.

1\.Be careful when you decide which storage solution is correct for your needs. These two services serve very different storage needs. Amazon S3 is designed for frequent, low-latency access to your data, but Amazon S3 Glacier is designed for low-cost, long-term storage of infrequently accessed data.

2\.The maximum item size in Amazon S3 is 5 TB, but Amazon S3 Glacier can store items that are up to 40 TB.

3\.Because Amazon S3 gives you faster access to your data, the storage cost per gigabyte is higher than it is with Amazon S3 Glacier.

4\.While both services have per-request charges, Amazon S3 charges for **PUT, COPY, POST, LIST, GET** operations. In contrast, Amazon S3 Glacier charges for **UPLOAD** and **retrieval** operations.

5\.Because Amazon S3 Glacier was designed for less-frequent access to data, it costs more for each retrieval request than Amazon S3. 


**Server-side Encryption**

Another important difference between Amazon S3 and Amazon S3 Glacier is how data is encrypted. Server-side encryption is focused on protecting data at rest. With both solutions, you can securely transfer your data over HTTPS. Any data that is archived in Amazon S3 Glacier is encrypted by default. With Amazon S3, your application must initiate server-side encryption. You can accomplish server-side encryption in Amazon S3 in several ways:

•Server-side encryption with **Amazon S3-managed encryption keys** (**SSE-S3**) employs strong multi-factor encryption. Amazon S3 encrypts each object with a unique key. As an additional safeguard, it encrypts the key with a master key that it regularly rotates. Amazon S3 server-side encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data.

•

•Using server-side encryption with **Customer-provided Encryption Keys (SSE-C)** enables you to set your own encryption keys. You include the encryption key as part of your request, and Amazon S3 manages both encryption (as it writes to disks), and decryption (when you access your objects).

•

•Using server-side encryption with **AWS Key Management Service** **(AWS KMS)** is a service that combines secure, highly available hardware and software to provide a key management system that is scaled for the cloud. AWS KMS uses **Customer Master Keys (CMKs)** to encrypt your Amazon S3 objects. You use AWS KMS through the **Encryption Keys** section in the IAM console. You can also access AWS KMS through the API to centrally create encryption keys, define the policies that control how keys can be used, and audit key usage to prove that they are being used correctly. You can use these keys to protect your data in Amazon S3 buckets.

**Security with Amazon S3 Glacier**

By default, only you can access your data. You can enable and control access to your data in Amazon S3 Glacier by using IAM. You set up an IAM policy that specifies user access.











**Module 8: Databases**

**Section 1: Amazon Relational Database Service**

**Unmanaged vs Managed Services**

AWS solutions typically fall into one of two categories: unmanaged or managed.



Unmanaged services are typically provisioned in discrete portions as specified by the user. You must manage how the service responds to changes in load, errors, and situations where resources become unavailable. Say that you launch a web server on an Amazon Elastic Compute Cloud (Amazon EC2) instance. Because Amazon EC2 is an unmanaged solution, that web server will not scale to handle increased traffic load or replace unhealthy instances with healthy ones unless you specify that it use a scaling solution, such as AWS Automatic Scaling. The benefit to using an unmanaged service is that you have more fine-tuned control over how your solution handles changes in load, errors, and situations where resources become unavailable.



Managed services require the user to configure them. For example, you create an Amazon Simple Storage Service (Amazon S3) bucket and then set permissions for it. However, managed services typically require less configuration. Say that you have a static website that you host in a cloud-based storage solution, such as Amazon S3. The static website does not have a web server. However, because Amazon S3 is a managed solution, features such as scaling, fault-tolerance, and availability would be handled automatically and internally by Amazon S3. 

**Challenges of Relational Databases**

When you run your own relational database, you are responsible for several administrative tasks, such as server maintenance and energy footprint, software, installation and patching, and database backups. You are also responsible for ensuring high availability, planning for scalability, data security, and operating system (OS) installation and patching. All these tasks take resources from other items on your to-do list, and require expertise in several areas. 

**Amazon RDS**

Amazon RDS is a managed service that sets up and operates a relational database in the cloud.

To address the challenges of running an unmanaged, standalone relational database, AWS provides a service that sets up, operates, and scales the relational database without any ongoing administration. Amazon RDS provides cost-efficient and resizable capacity, while automating time-consuming administrative tasks.

Amazon RDS enables you to focus on your application, so you can give applications the performance, high availability, security, and compatibility that they need. With Amazon RDS, your primary focus is your data and optimizing your application. 

**From On-premises Databases to Amazon RDS**

What does the term **managed services** mean?

When your database is on premises, the database administrator is responsible for everything. Database administration tasks include optimizing applications and queries; setting up the hardware; patching the hardware; setting up networking and power; and managing heating, ventilation, and air conditioning (HVAC).

If you move to a database that runs on an **Amazon Elastic Compute Cloud (Amazon EC2) instance**, you no longer need to manage the underlying hardware or handle data center operations. However, you are still responsible for patching the OS and handling all software and backup operations.

If you set up your database on **Amazon RDS** or **Amazon Aurora**, you reduce your administrative responsibilities. By moving to the cloud, you can automatically scale your database, enable high availability, manage backups, and perform patching. Thus, you can focus on what really matters most—optimizing your application.

**Managed Services Responsibilities**

With Amazon RDS, you manage your application optimization. AWS manages installing and patching the operating system, installing and patching the database software, automatic backups, and high availability.

AWS also scales resources, manages power and servers, and performs maintenance.

Offloading these operations to the managed Amazon RDS service reduces your operational workload and the costs that are associated with your relational database. You will now go through a brief overview of the service and a few potential use cases. 



**Amazon RDS DB Instances**

The basic building block of Amazon RDS is the database instance. A **database instance** is an isolated database environment that can contain multiple user-created databases. It can be accessed by using the same tools and applications that you use with a standalone database instance. The resources in a database instance are determined by its database instance class, and the type of storage is dictated by the type of disks.

Database instances and storage differ in performance characteristics and price, which enable you to customize your performance and cost to the needs of your database. When you choose to create a database instance, you must first specify which database engine to run. Amazon RDS currently supports six databases: MySQL, Amazon Aurora, Microsoft SQL Server, PostgreSQL, MariaDB, and Oracle. 

**Amazon RDS In a Virtual Private Cloud (VPC)**

You can run an instance by using **Amazon Virtual Private Cloud (Amazon VPC).** When you use a virtual private cloud (VPC), you have control over your virtual networking environment.

You can select your own IP address range, create subnets, and configure routing and access control lists (ACLs). The basic functionality of Amazon RDS is the same whether or not it runs in a VPC. Usually, the database instance is isolated in a private subnet and is only made directly accessible to indicated application instances. Subnets in a VPC are associated with a single Availability Zone, so when you select the subnet, you are also choosing the Availability Zone (or physical location) for your database instance. 

**High Availability with Multi-AZ Deployment**

One of the most powerful features of Amazon RDS is the ability to configure your database instance for high availability with a Multi-AZ deployment. After a Multi-AZ deployment is configured, Amazon RDS automatically generates a standby copy of the database instance in another Availability Zone within the same VPC. After seeding the database copy, transactions are synchronously replicated to the standby copy. Running a database instance in a Multi-AZ deployment can enhance availability during planned system maintenance, and it can help protect your databases against database instance failure and Availability Zone disruption. 

Therefore, if the main database instance fails in a Multi-AZ deployment, Amazon RDS automatically brings the standby database instance online as the new main instance. The synchronous replication minimizes the potential for data loss. Because your applications reference the database by name by using the Amazon RDS Domain Name System (DNS) endpoint, you don't need to change anything in your application code to use the standby copy for failover. 

**Amazon RDS Read Replicas**

Amazon RDS also supports the creation of read replicas for MySQL, MariaDB, PostgreSQL, and Amazon Aurora. Updates that are made to the source database instance are asynchronously copied to the read replica instance. You can reduce the load on your source database instance by routing read queries from your applications to the read replica. Using read replicas, you can also scale out beyond the capacity constraints of a single database instance for read-heavy database workloads. Read replicas can also be promoted to become the master database instance, but this requires manual action because of asynchronous replication.

Read replicas can be created in a different Region than the master database. This feature can help satisfy disaster recovery requirements or reduce latency by directing reads to a read replica that is closer to the user. 

**Use Cases**

Amazon RDS works well for web and mobile applications that need a database with high throughput, massive storage scalability, and high availability. Because Amazon RDS does not have any licensing constraints, it fits the variable usage pattern of these applications. For small and large ecommerce businesses, Amazon RDS provides a flexible, secure, and low-cost database solution for online sales and retailing. Mobile and online games require a database platform with high throughput and availability. Amazon RDS manages the database infrastructure, so game developers do not need to worry about provisioning, scaling, or monitoring database servers. 

**When to Use Amazon RDS**

Use Amazon RDS when your application requires:

•Complex transactions or complex queries

•A medium to high query or write rate – up to 30,000 IOPS (15,000 reads + 15,000 writes)

•No more than a single worker node or shard

•High durability



Do not use Amazon RDS when your application requires:

•Massive read/write rates (for example 150,000 writes per second)

•Sharding due to high data size or throughput demands

•Simple GET or PUT requests and queries that a NoSQL database can handle

•Or, relational database management system (RDBMS) customization



For circumstances when you should not use Amazon RDS, consider either using a NoSQL database solution (such as DynamoDB) or running your relational database engine on Amazon EC2 instances instead of Amazon RDS (which will provide you with more options for customizing your database).

**Amazon RDS: Clock-hour billing and database characteristics**

When you begin to estimate the cost of Amazon RDS, you must consider the clock hours of service time, which are resources that incur charges when they are running (for example, from the time you launch a database instance until you terminate the instance).



Database characteristics should also be considered. The physical capacity of the database you choose will affect how much you are charged. Database characteristics vary depending on the database engine, size, and memory class. 

**Amazon RDS: DB purchase type and multiple DB instances**

Consider the database purchase type. When you use On-Demand Instances, you pay for compute capacity for each hour that your database instance runs, with no required minimum commitments. With Reserved Instances, you can make a low, one-time, upfront payment for each database instance you want to reserve for a 1-year or 3-year term.



Also, you must consider the number of database instances. With Amazon RDS, you can provision multiple database instances to handle peak loads. 

**Amazon RDS: Storage**

Consider provisioned storage. There is no additional charge for backup storage of up to 100 percent of your provisioned database storage for an active database instance. After the database instance is terminated, backup storage is billed per GB, per month.



Also consider the amount of backup storage in addition to the provisioned storage amount, which is billed per GB, per month. 

**Amazon RDS: Deployment type and data transfer**

Also consider the number of input and output requests that are made to the database.



Consider the deployment type. You can deploy your DB instance to a single Availability Zone (which is analogous to a standalone data center) or to multiple Availability Zones (which is analogous to a secondary data center for enhanced availability and durability). Storage and I/O charges vary, depending on the number of Availability Zones that you deploy to.



Finally, consider data transfer. Inbound data transfer is free, and outbound data transfer costs are tiered.



Depending on the needs of your application, it’s possible to optimize your costs for Amazon RDS database instances by purchasing Reserved Instances. To purchase Reserved Instances, you make a low, one-time payment for each instance that you want to reserve. As a result, you receive a significant discount on the hourly usage charge for that instance.

**Section 2: Amazon DynamoDB**

**Relational vs non-relational databases**

With DynamoDB, this module transitions from relational databases to non-relational databases. Here is a review of the differences between these two types of databases:

•A **relational database** (RDB) works with structured data that is organized by tables, records, and columns. RDBs establish a well-defined relationship between database tables. RDBs use structured query language (SQL), which is a standard user application that provides a programming interface for database interaction. Relational databases might have difficulties scaling out horizontally or working with semistructured data, and might also require many joins for normalized data.

•A **non-relational database** is any database that does not follow the relational model that is provided by traditional relational database management systems (RDBMS). Non-relational databases have grown in popularity because they were designed to overcome the limitations of relational databases for handling the demands of variable structured data. Non-relational databases scale out horizontally, and they can work with unstructured and semistructured data.

Here is a look at what DynamoDB offers.



**What is Amazon DynamoDB?**

DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit-millisecond latency at any scale.

Amazon manages all the underlying data infrastructure for this service and redundantly stores data across multiple facilities in a native US Region as part of the fault-tolerant architecture. With DynamoDB, you can create tables and items. You can add items to a table. The system automatically partitions your data and has table storage to meet workload requirements. There is no practical limit on the number of items that you can store in a table. For instance, some customers have production tables that contain billions of items.

One of the benefits of a NoSQL database is that items in the same table can have different attributes. This gives you the flexibility to add attributes as your application evolves. You can store newer format items side by side with older format items in the same table without needing to perform schema migrations.

As your application becomes more popular and as users continue to interact with it, your storage can grow with your application's needs. All the data in DynamoDB is stored on solid state drives (SSDs) and its simple query language enables consistent low-latency query performance. In addition to scaling storage, DynamoDB also enables you to provision the amount of read or write throughput that you need for your table. As the number of application users grows, DynamoDB tables can be scaled to handle the increased numbers of read/write requests with manual provisioning. Alternatively, you can enable automatic scaling so that DynamoDB monitors the load on the table and automatically increases or decreases the provisioned throughput.

Some additional key features include global tables that enable you to automatically replicate across your choice of AWS Regions, encryption at rest, and item Time-to-Live (TTL). 

DynamoDB is a fully managed NoSQL database service. Amazon manages all of the underlying data infrastructure for this service and redundantly stores data across multiple facilities within a native US region as part of the fault-tolerant architecture. With DynamoDB, you can create tables and items. You can add items to a table. The system automatically partitions your data and has table storage to meet the workload requirements. There is no practical limit on the number of items you can store in a table. For instance, some customers have production tables that contain billions of items.

One of the benefits of a NoSQL database is that items in the same table may have different attributes. This gives you the flexibility to add attributes as your application evolves. You can have newer format items stored side by side with older format items in the same table without needing to perform schema migrations.

As your application becomes more popular and as users continue to interact with it, your storage can grow with your application's needs. All of the data in DynamoDB is stored on solid-state drives and its simple query language allows for consistent low-latency query performance. In addition to scaling storage, DynamoDB also allows you to provision the amount of read or write throughput you need for your table. As the number of application users grow, DynamoDB tables can be scaled to handle the increased numbers of read and write requests with manual provisioning. Alternatively, you can enable automatic scaling so that DynamoDB monitors the load on the table and automatically increases or decreases the provisioned throughput.

Some additional key differentiating features include global tables that enable you to automatically replicate across your choice of AWS regions, encryption at rest, and item Time-to-Live (TTL). 

**Amazon DynamoDB Core Components**

The core DynamoDB components are tables, items, and attributes.

•A table is a collection of data.

•Items are a group of attributes that is uniquely identifiable among all the other items.

•Attributes are a fundamental data element, something that does not need to be broken down any further.



DynamoDB supports two different kinds of primary keys.

The **partition key** is a simple primary key, which is composed of one attribute called the **sort** key.

The partition key and sort key are also known as the **composite primary key**,** which is composed of two attributes.

**Section 3: Amazon Redshift**

Amazon Redshift is a fast, fully managed data warehouse that makes it simple and cost-effective to analyze all your data by using standard SQL and your existing business intelligence (BI) tools. Here is a look at Amazon Redshift and how you can use it for analytic applications.

Analytics is important for businesses today, but building a data warehouse is complex and expensive. Data warehouses can take months and significant financial resources to set up.

Amazon Redshift is a fast and powerful, fully managed data warehouse that is simple and cost-effective to set up, use, and scale. It enables you to run complex analytic queries against petabytes of structured data by using sophisticated query optimization, columnar storage on high-performance local disks, and massively parallel query execution. Most results come back in seconds.

The leader node manages communications with client programs and all communication with compute nodes. It parses and develops execution plans to carry out database operations—specifically, the series of steps that are needed to obtain results for complex queries. The leader node compiles code for individual elements of the execution plan and assigns the code to individual compute nodes. The compute nodes execute the compiled code and send intermediate results back to the leader node for final aggregation.



Like other AWS services, you only pay for what you use. You can get started for as little as 25 cents per hour and, at scale, Amazon Redshift can deliver storage and processing for approximately $1,000 dollars per terabyte per year (with 3-Year Partial Upfront Reserved Instance pricing).



The Amazon Redshift Spectrum feature enables you to run queries against exabytes of data directly in Amazon S3.

It is straightforward to automate most of the common administrative tasks to manage, monitor, and scale your Amazon Redshift cluster—which enables you to focus on your data and your business.

Scalability is intrinsic in Amazon Redshift. Your cluster can be scaled up and down as your needs change with a few clicks in the console.



Security is the highest priority for AWS. With Amazon Redshift, security is built in, and it is designed to provide strong encryption of your data both at rest and in transit. 

Finally, Amazon Redshift is compatible with the tools that you already know and use. Amazon Redshift supports standard SQL. It also provides high-performance Java Database Connectivity (JDBC) and Open Database Connectivity (ODBC) connectors, which enable you to use the SQL clients and BI tools of your choice.








**Section 4: Amazon Aurora**

Amazon Aurora is a MySQL- and PostgreSQL-compatible relational database that is built for the cloud. It combines the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases. Using Amazon Aurora can reduce your database costs while improving the reliability and availability of the database. As a fully managed service, Aurora is designed to automate time-consuming tasks like provisioning, patching, backup, recovery, failure detection, and repair.

It is highly available and it offers a fast, distributed storage subsystem. Amazon Aurora is straightforward to set up and uses SQL queries. It is designed to have drop-in compatibility with MySQL and PostgreSQL database engines so that you can use most of your existing database tools with little or no change.



Amazon Aurora is a pay-as-you-go service, which means that you only pay for the services and features that you use. It’s a managed service that integrates with features such as AWS Database Migration Service (AWS DMS) and the AWS Schema Conversion Tool. These features are designed to help you move your dataset into Amazon Aurora.

Amazon Aurora is designed to be highly available: it stores multiple copies of your data across multiple Availability Zones with continuous backups to Amazon S3. Amazon Aurora can use up to 15 read replicas can be used to reduce the possibility of losing your data. Additionally, Amazon Aurora is designed for instant crash recovery if your primary database becomes unhealthy.

After a database crash, Amazon Aurora does not need to replay the redo log from the last database checkpoint. Instead, it performs this on every read operation. This reduces the restart time after a database crash to less than 60 seconds in most cases.

With Amazon Aurora, the buffer cache is moved out of the database process, which makes it available immediately at restart. This reduces the need for you to throttle access until the cache is repopulated to avoid brownouts.

