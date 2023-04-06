# Module 01 #

## Understanding Systems Operations ##

**Systems operations responsibilities and tasks:**

- Build
- Test
- Deploy
- Monitor
- Maintain
- Safeguard

**Automations of systems operations enables:**

- Repeatable deployment of infrastructure and applications on demand.
- Creation of self-describing systems.
- Building well tested secure systems.
- Script, program or template >
  - Development
  - Test
  - Production

## Key AWS services for systems operations ##

**Network - Amazon Virtual Private Cloud (Amazon VPC):**

- Virtual networks
- Logically isolated
- Configurable key features:
  - IP ranges, routing, gateways, and security settings
**Compute - Amazon Elastic Compute Cloud (Amazon EC2):**
- Virtual computing environments
- Amazon Machine Images (AMIs)
- Scalable
- Optimizable
**Access - AWS Identity and Access Management (IAM):**
- Manage access and authentication
- Users, groups, roles, and policies
- Identity federation

## Scope of Amazon Web Services ##

**Region:**

- Amazon Simple Storage Service (Amazon S3) buckets
- Amazon Machine Images (AMIs)
- Amazon CloudWatch metrics
- Amazon Elastic Block Store (Amazon EBS) snapshots
- Amazon ElastiCache clusters
- Amazon Virtual Private Cloud (VPC)

**Global:**

- IAM users, groups, and roles
- Amazon Route 53 hosted zones and record sets
- Amazon CloudFront distributions

**Availability Zone:**

- Amazon EC2 instances
- Amazon EBS volumes
- Amazon Relational Database Service (Amazon RDS) database instances
- Subnets

## Service Limits on AWS ##

Limit potential excessive charges and keep the AWS network healthy

**Soft limits:**

- Can be changed on request to AWS Support
- Exceeding some soft limits might result in performance degredation

**Hard limits:**

- Cannot be changed

## Introduction to IAM ##

**AWS Identity and Access Management (IAM)** allows you to centrally manage authentication and access to AWS resources.

- Offered as a feature of an AWS account at no charge
- Create **users, groups,** and **roles**
- Apply **policies** to them to control their access to AWS resources

## IAM: Authentication ##

To provide *programmatic* access, create an *access key ID* and a *secret access key*, and provide them to the user. With these two items, the user will have access to:

- AWS application programming interfaces (APIs)
- AWS Command Line Interface (AWS CLI)
- AWS software development kits (SDKs)

To provide *AWS Management Console* access, assign the user a user name and password. The AWS Management Console provides a simple web interface for AWS. If the IAM user account has *multi-factor authentication (MFA)* enabled - which is recommended for added security - the user will be prompted for an additional authentication code after providing their user name and password.

## Types of Security Credentials ##

- **Email address and password:** Associated with **AWS account (root)**
- **IAM user name and password:** Used for accessing the **AWS Management Console**
- **Access keys:** Typically used with the **AWS CLI** and programmatic requests like **APIs** and **SDKs**
- **Multi-factor authentication (MFA):** Extra layer of **security**. Can be enabled for **root account** and IAM users.
- **Key pairs:** Used only for specific AWS services like Amazon EC2.

## Policies and Permissions ##

The four policy types, which indicate the type of permissions that are defined fo rthe assigned users, are listed here in order of popular usuage:

- **Identity-based policies** allow a user to attach managed and inline policies to IAM identities, such as users or the groups to which users belong. A user can also attach identity-based policies to roles. Policy categories, to IAM identities that include:
  - Users
  - Groups that users belong to
  - Roles

- **Resource-based policies** allow a user to attach inline policies to resources. The most common examples of resource-based policies are Amazon S3 bucket policies and IAM role trust policies. Resource policies are JavaScript Object Notation (JSON) policy documents.
  - Resource-level permissions are only avaiable for some AWS services and resources and provide granular access control over specific objects within an AWS service.
  - Resource-level permissions do not always allow all actions.
    - For EC2 instances, actions such as Reboot, Start, Stop, and Terminate can be specified.
    - Actions such as RunInstances cannot be specified, because you do not know the InstanceID before the RunInstances call is complete. Therefore, RunInstances applies to EC2 as a whole service, but not as a specific resource.

- **AWS Organizations service control policies (SCPs)** apply permissions boundaries to **AWS Organizations** or **organizational units (OUs).**

- **Access control lists (ACLs)** can also be used to control which principals can access a resource. ACLs are similar to resource-based policies, although they are the only policy type that does not use the JSON policy document structure. ACLs do not use the JSON policy document structure.

**Policies evalute the following logic:**

- Authenticate principal
- Process request context:
  - Environment data
  - Resources data
  - Actions
  - Resources
  - Principal
- Evaluate policies based on:
  - Policy type
  - Policy category
- Allow or deny request  

The *evaluation order of the policies* has no effect on outcome.

## Using IAM Roles ##

There are three ways to use a role:

- Interactively in the IAM section of the AWS Management Console
- Programmatically with the AWS CLI
- Via the AWS SDKs (API calls)

An application or a service such as Amazon EC2 can *assume* a role by requesting temporary security credentials for a role that the service can use to make programmatic requests to AWS.

IAM roles also support single sign-on solutions. With an identity provider, user identities can be managed outside of AWS, and these external user identities could be permissions to access resources in the AWS account.

## IAM User Assume Role ##

IAM users in the account can assume an IAM role to temporarily use the permissions of the role in the console. The user gives up their original permissions and thakes on the permissions assigned to the role. When the user exits the role, their original permissions are restored. A user can switch roles to access resources in the AWS account, or even switch roles to access resources in other AWS accounts, which is called *cross-account access.*

Cross-account access grants access from another AWS account. This could b ean account you own, or an account owned by another person. If the account is owned by another person or organization, it is a best practice to also provide a shared secret called an *external ID.* This stops one AWS account from guessting the role ARN for a different account and handing that to a common deputized AWS account. By configuring roles, an IAM administrator can grant the needed access without sharing the permanent AWS security credentials.

## IAM Best Practices ##

Here are some best practices for IAM:

- Avoid using the root account credentials for daily administration. Instead, when setting up a new account, define at least one new IAM user. Then, grant the user or users access so that most day-to-day tasks can be done using the IAM user credentials.
- Delegate administration functions following the principle of least-privilege. Only grant access to services that are needed, and limit permissions within those services to only the parts needed. Additional rights can always be granted over time if the need arises.
- Use IAM roles to provide cross-account access. Configure strong password poilicies, enable MFA for any privileged users, and rotate credentials regularly.
- MFA is a good practice to implement for security purposes.

## AWS Command Line Interface (AWS CLI) ##

