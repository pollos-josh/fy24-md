[[Index]]
---

# Udemy Course

## Azure DDoS Protection

Offers protection for Azure Resources including DDoS protection, always-on monitoring, and automatic attack mitigation.

> [!note] DDoS pricing is $2,944 / month with no upfront commitment

## Which of the following Help You save Money by Committing to One-year or Three-year Plans for Multiple Products?

**Azure Reservations** is an option for predictable workloads. It allows you to commit specific resources for one or three years up-front with up to **72% discounts** compared to pay-as-you-go pricing.

## True or False: According to the Microsoft Online Subscription Agreement, the Customer is Responsible for Maintaining the Confidentiality of Any Non-public Authentication Credentials Associated with Use of the Online Services.

**True** - this is true for various Microsoft services, including Azure.

> [!quote] Microsoft Service Agreement
> **e. Responsibility for your accounts.** You are responsible for maintaining the confidentiality of any non-public authentication credentials associated with your use of the Online Services. You will promptly notify customer support about any possible misuse of your accounts or authentication credentials or any security incident related to the Online Services.

This means that customers are accountable for their:

- Passwords and login details
- Sharing of credentials
- Potential phishing attempts
- Reporting suspicious activity

## Which of the following Refers to the Ability to Quickly Expand and Decrease Computer Processing, Memory, and Storage Resources to Meet Changing Demands without Worrying about Capacity Planning and Engineering for Peak Usage in Microsoft Azure?

**Elasticity** - refers to the ability to quickly scale up or down dynamically based on demand. This allows users to handle workloads without concern about underor over-provisioning resources.

## Which of the following Are Key Advantages of a Hybrid Cloud in Microsoft Azure?

### Advantages

- **Control**: Your organization can maintain a private infrastructure for sensitive assets.
- **Lower costs**: There is no need to purchase hardware or software, and an organization pays only for the services it uses.

### Not Advantages

- Improved security: Resources are not shared with others, so higher levels of control and security are possible.
- Cost-effectiveness: Thanks to the scalability of the public cloud, you pay for extra computing power only when needed.

> [!warning] Explanation
> - **Improved security:** While a hybrid cloud can offer some security benefits due to isolated private infrastructure, security ultimately depends on your specific implementation and overall security posture. Additionally, security vulnerabilities or breaches can still occur in either the public or private cloud, so a comprehensive security strategy across both environments is essential.
> - **Lower costs (no hardware/software purchase):** This statement isn't entirely accurate. A hybrid cloud still requires investment and overhead in maintaining your on-premises infrastructure, including hardware, software licensing, and IT staff. While you might avoid some upfront costs compared to a purely public cloud approach, there are ongoing expenses involved.

## XYZ Organization Runs Some Infrastructure in Local Data Centers (on premises) and Some Infrastructure in an Azure Virtual Network (cloud). Which of the following Azure Services Enables You to Use a Hybrid Cloud Deployment Model?

- **VPN gateway**
- Service endpoint
- Virtual CDN endpoint
- Private endpoint

> [!success] **VPN gateway**
> - **VPN gateway:** Creates a secure, encrypted tunnel between your on-premises network and the Azure virtual network. This allows resources in both environments to communicate securely, facilitating hybrid cloud operations.
> - **Service endpoint:** Restricts outbound traffic from a resource in Azure to only reach specific services within a virtual network. This doesn't directly bridge your on-premises network with Azure.
> - **Virtual CDN endpoint:** Accelerates the delivery of static content from an Azure CDN closer to users globally. It doesn't connect on-premises infrastructure to Azure for hybrid deployments.
> - **Private endpoint:** Creates a private IP address for an Azure resource within a virtual network, making it accessible only through private links without internet exposure. It doesn't directly connect to on-premises networks.

## Which of the following is a Limitless Analytics Service in Microsoft Azure that Brings together Enterprise Data Warehousing and Big Data Analytics together under the Same Umbrella?

- Azure VMs
- **Azure Postgres DB**
- Azure Synapse
- Azure Data Store

> [!error] Azure Synapse
> Azure Synapse offers a unified platform for both enterprise data warehousing and big data analytics, handling:
> - ***Data Warehousing***: structured, relational data for historical analysis and processing
> - ***Big Data Analytics***: unstructured, semi-structured, and large-scale data for advanced insights and machine learning

## Which of These Are NOT Advantages of Deploying a Private Cloud in Microsoft Azure Cloud Platform Using portal.azure.com or Cloud Shell?

- Having control over security and owning the data
- Meeting strict security compliance, or legal requirements
- Receiving high scalability and agility by default
- Having no responsibility for maintenance and hardware updates

> [!warning] Having Control / Meeting Strict Security Requirements
> - **Having control over security and owning the data:** While deploying a private cloud in Azure does provide a greater degree of control over security compared to a public cloud environment, it's important to remember that you are still relying on Azure's underlying infrastructure and security practices. Additionally, while you **control** the data, Azure does store your data in its data centers, so complete ownership isn't accurate.
> - **Meeting strict security, compliance, or legal requirements:** While a private cloud in Azure can be suitable for meeting strict security requirements, it's crucial to carefully evaluate whether it completely fulfills your specific compliance or legal needs. Some regulations might require additional controls or on-premises data storage that a private cloud in Azure alone may not offer.

## Which of the following Solutions is Used to Help Model Data from Sources such as Data Warehouses and Data Lakes to Train Machine Learning Models in Microsoft Azure Platform?

- Azure Databricks
- HDInsight
- **Azure Synapse Analytics**
- Cognitive Services

> [!success] Azure Synapse Analytics
> It offers capabilities for both data integration and data modeling, making it ideal for preparing data for machine learning models:
> 
> > [!tip] Azure Synapse is most suited for big-data and noSQL services for machine learning and data modelling.

## Azure Dedicated Host, Azure Sentinel, and Network Service Group

### Azure Dedicated Host

A dedicated physical server in an Azure data center reserved exclusively for virtual machines. Unlike normal VMs, they do not share space with other customers.

> [!example] Benefits
> Increase isolation and security
> Dedicated performance
> Flexible resource management
> Cost Optimization

### Network Service Group

A security role applied to *network interfaces* attached to VMs within a virtual network. They control inbound and outbound network traffic like firewalls.

NSGs enable you to:

- **Define granular access control:** Specify which protocols, ports, and source/destination IP addresses are allowed or denied access to your VMs.
- **Segment your VNet:** Create multiple NSGs for different groups of VMs within the same VNet, isolating traffic flow and enhancing security.
- **Improve manageability:** Apply consistent security policies across multiple VMs by managing rules in a single NSG instead of configuring each VM individually.

### Azure Sentinel

A cloud native **SIEM** and **SOAR** solution.

#### SIEM

 - **Security Information and Event Management (SIEM):** Azure Sentinel excels at ingesting and analyzing security data from a wide range of sources, including Azure services, on-premises infrastructure, and other cloud providers. It uses this data to detect potential threats and provide insights into your security posture.
 - **Log aggregation and analysis:** It ingests and stores security data from various sources in a central location, enabling efficient analysis and correlation of events.
 - **Security analytics and threat detection:** It employs built-in AI and machine learning to identify suspicious activities, correlate events, and generate alerts about potential threats.
 - **Security incident investigation:** It provides tools and dashboards to investigate security incidents efficiently, track progress, and collaborate with your team.

#### SOAR

 - **Security Orchestration, Automation, and Response (SOAR):** While not as comprehensive as dedicated SOAR tools, Azure Sentinel offers limited automation capabilities that can streamline your incident response process.
- **Playbooks and automation:** It allows you to build playbooks with automated actions triggered by specific events or alerts. These playbooks can automate tasks like:
    - *Disabling compromised user accounts.*
    - *Enforcing network isolation.*
    - *Sending notifications to security teams.*
- **Integration with other tools:** It integrates with various security tools and services, enabling you to automate responses across different platforms.

> [!tip]
> Azure Sentinel can collect Windows Defender logs from Azure Virtual Machines.

## Azure Defender

1. **1. Security Alerts and Incidents Management are available only to those who pay for a Premium License of Azure Defender:**
	1. **False.** Security Alerts and Incidents Management are **available for free with any Azure subscription**, even without a paid Azure Defender license. However, the free tier has limited features, such as only storing alerts for 30 days and limited access to investigation tools. The Premium tier of Azure Defender offers additional features like threat intelligence, extended alert storage, and advanced investigation capabilities.
2. **2. Azure Defender costs $15 per month per resource:**
	1. **False.** Azure Defender pricing is not per resource, but rather based on the **resource type and the service plan you choose**. For example, Azure Defender for Servers starts at $3.08 per month for a standard VM (Standard_D2s v2), and Azure Defender for Azure SQL Database starts at $1.62 per month per database. The Premium tier pricing varies depending on the resource type.
3. **3. You can actively manage all resources in a subscription through inventory:**
	1. **Partially true.** You can view an inventory of all resources in your subscription through the Azure portal or Azure Resource Explorer. However, this isn't the same as **actively managing** them. Managing resources involves tasks like starting and stopping VMs, applying security policies, or updating software. While you can access information about your resources through inventory, you might need to use different tools or services to perform specific management tasks.

## Which of the following Microsoft Network Security Products Utilize IP Addresses and Domains Data to Protect Victims of Attacks? The Data Collected Becomes part of the Microsoft Threat Intelligence Feed for Azure Services.

- Azure DDoS Basic
- **Azure Security Center**
- Azure Firewall
- Azure Dedicated Hosts

> [!success] Azure Security Center
> This comprehensive security solution continuously analyzes security data from your Azure resources, including network traffic. It leverages the Microsoft Threat Intelligence Feed to identify and block malicious IP addresses and domains associated with known threats. This data also contributes back to the Threat Intelligence Feed, helping to protect other Azure users.

## TCO Vs Price Calculator Vs Azure Reservations

**Scope**: Pricing Calculator focuses on Azure service costs, while TCO Calculator includes broader migration-related costs.

**Detail**: Pricing Calculator is specific to individual Azure services, while TCO Calculator offers a more holistic view.

**Discounts**: Pricing Calculator doesn't offer discounts, while Azure Reservations can significantly reduce costs.

## Which of the following is not a Type of Microsoft Azure Firewall Rule?

- NAT rules
- Network rules
- **Application rules**
- DDoS rule

> [!error] DDoS Rule
> While commonly used in Azure security solutions, it's not a specific Azure Firewall rule type. DDoS protection often works by analyzing network traffic at a broader level than individual firewall rules. Azure offers DDoS protection services but not dedicated DDoS rules within the Azure Firewall itself.

## NSG Traffic Range Upper Limit

**65,535** - - Network security groups (NSGs) use ports to define allowed or denied traffic. Ports are identified by numbers ranging from 0 to 65,535.

## True or False

**1. You must have an active subscription to download items from Azure Marketplace:**

**True.** To download and deploy items from Azure Marketplace, you need an active Azure subscription. This includes both paid and free subscriptions, but free subscriptions often have limitations on the resources you can use.

**2. Even if you have a free virtual machine, you still have to pay for storage instances:**

**True and False.** It depends on the type of storage you're using:

- **Managed disks:** Yes, even with a free VM, you will be charged for managed disks attached to it. Free subscriptions come with a small amount of free managed disk space, but exceeding that will incur charges.
- **Unmanaged disks:** If you're using unmanaged disks (available in classic VMs only), you won't be charged for the disk itself, but you will be charged for the storage used.

**3. The only place you can access Azure Marketplace is from portal.azure.com:**

**False.** You can access Azure Marketplace through several ways:

- **Azure Portal:** This is the primary way, offering a user-friendly interface for browsing and deploying solutions.
- **Azure Resource Manager (ARM) Templates:** You can use ARM templates to automate deployments from the Marketplace.
- **Azure PowerShell or Azure CLI:** These command-line tools allow programmatic access to the Marketplace for scripting deployments.
- **REST API:** The Azure Marketplace API can be used to integrate Marketplace functionalities into other applications or tools.

# CrackCert Test

## What is the GDPR

**General Data Protection Regulation** gives rights to people to manage personal data collected by an organization. These rights are exercised by a *Data Subject Request (DSR)*. The organization is also required to provide timely information regarding DSRs and data breaches, and perform *Data Protection Impact Assessments (DPIAs)*.

> [!note] When implementing or assessing GDPRs, you should consider:
> - Developing or evaluating your GDPR compliance policy
> - Assessing the security of your organization
> - Who is your data controller?
> - What data security may you have to perform?

## Resource Inheritance

Inheritance is top-down, which means resources inherit from the parent.

A resource can have multiple locks and tags.

> [!tip] A resource can only have a maximum of 50 tag name-value pairs.
> If you need to apply more than 50, use a JSON string for the tag value.

## Data Storage

Azure maintains at least 3 copies of data within the datacenter associated with the storage account.

## Azure Blueprints Vs ARM

### Azure Blueprints

**Purpose**: Standardize and govern deployments across multiple subscriptions.

**Features**:

- Package resource groups, policies, role assignments, and ARM templates.
- Enforce consistent configurations and compliance.
- Version control and track deployments.
- Apply to multiple subscriptions simultaneously.
- Limited flexibility for individual customization.
**Who should use it**: Organizations needing standardized, repeatable deployments with strong governance and compliance requirements.

### ARM Templates

 **Purpose:** Define infrastructure as code for individual deployments.

 **Features:**

- Highly flexible and customizable.
- Can target specific resources or groups.
- More complex to manage and enforce governance.
- No native version control or audit trails.
 **Who should use it:** Organizations needing flexibility for unique deployments or who don't need strict governance at the subscription level.

### Which to Choose

 **Blueprints**

 - Standardized configurations
 - Governance and compliance
 - Auditing and tracking deployments
 - Pre-built blueprints for common scenarios
 **ARM**
 - Flexibility in customization
 - Targeted deployments
 - More control in deployment process

 > [!tip]
 > Blueprints can use ARM templates

## Azure Machine Learning Vs Azure Synapse

### Azure Machine Learning

**Pros**

- Build, deploy, and train machine learning models at scale. It is a *PaaS* designed for Machine Learning.
- It has pre-built templates and AI components for fast development. It also has a specialized computing options for training models.

**Cons**

- Not ideal for general data analytics beyond model training.
- Can become costly for complex or large scale businesses.

### Azure Synapse

**Pros**

- Unified platform for data-warehousing, data analytics, and data integration.
- Able to handle normal structured/semi-structured and unstructured/big data.
- Serverless
- Best for: Data scientists, developers, and businesses building and deploying machine learning models for various applications.

**Cons**

- Machine learning not as comprehensive as *Azure Machine Learning* for complex models
- Learning curve steeper for specialized use cases
- **Best for:** Data analysts, data engineers, and businesses needing a comprehensive platform for data warehousing, analytics, and basic machine learning needs.

| **Azure Machine Learning** | **Azure Synapse Analytics** |  |
| :--: | :--: | :--: |
| *Primary Focus* | Machine learning | Data warehousing, big data analytics, data integration |
| *Strengths* | Pre-built components, MLOps, diverse compute options | Unified platform, scalability, handles various data types |
| *Weaknesses* | Costly for complex models, limited data analytics | Machine learning not as advanced as AML |
| *Best for* | Data scientists, developers, businesses building ML models | Data analysts, engineers, businesses with comprehensive data needs |
| *Machine Learning* | Dedicated service with extensive features | Basic capabilities, integrates with AML |

## Azure IoT

Enables you to control, monitor, and connect your *Internet of Things* assets at scale. It is able to take in data from millions of different sensors.

### Components

- Cloud services
	- Azure IoT Hub
	- Azure IoT Central
	- Azure Digital Twins
	- **Azure Machine Learning**
	- Azure Data Services
- Edge components
	- Azure IoT Edge
	- Azure Sphere
	- Windows for IoT
- SDKs

## Traffic Charges

All inbound data transfer is free-of-charge. All outbound data transfers are charged based on the table below. Users are also charged a fixed monthly rate port fee.

|Circuit bandwidth|Standard Price per month|Premium price per month|Inbound data transfer included|Outbound data transfer included|
|---|---|---|---|---|
|50 Mbps|$55|$130|Unlimited|None|
|100 Mbps|$110|$200|Unlimited|None|
|200 Mbps|$145|$295|Unlimited|None|
|500 Mbps|$290|$690|Unlimited|None|
|1 Gbps|$436|$1,186|Unlimited|None|
|2 Gbps|$872|$2,372|Unlimited|None|
|5 Gbps|$2,180|$5,180|Unlimited|None|
|10 Gbps|$3,400|$6,400|Unlimited|None|
