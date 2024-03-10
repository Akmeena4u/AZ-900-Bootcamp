in this his module explains the basic infrastructure components of Microsoft Azure. You'll learn about the physical infrastructure, how resources are managed, and have a chance to create an Azure resource.

# Learning objectives
1. Upon completion of this module, you will be able to:
2. Describe Azure regions, region pairs, and sovereign regions
3. Describe Availability Zones
4. Describe Azure datacenters
5. Describe Azure resources and Resource Groups
6. Describe subscriptions
7. Describe management groups
8. Describe the hierarchy of resource groups, subscriptions, and management groups

   ---
 ## What is Microsoft Azure

  Microsoft Azure is a cloud computing platform offered by Microsoft. It's essentially a giant online collection of resources that allows you to access a wide variety of services. These services can be broadly categorized into:

* **Compute:** This includes creating virtual machines, running code without managing servers (serverless computing), and batch processing for large tasks.

* **Storage:** Store all sorts of data in the cloud, from basic files to complex databases.

* **Networking:** Connect your cloud resources to each other, your on-premises data centers, and the internet securely.

* **Artificial intelligence:** Access powerful AI tools and pre-built models to integrate intelligence into your applications.

* **And many more:** There are services for web development, security, the Internet of Things (IoT), and much more. 

In short, Azure provides a comprehensive suite of tools to help you build, deploy, and manage your applications in the cloud. You can pay for only the services you use, making it a scalable and cost-effective solution.

--
## Get started with Azure accounts

#### Azure Free Student Account:
1. Offers free access to select Azure services for 12 months.
2. Includes a credit for the first 12 months and access to specific software developer tools.
3. No credit card required for sign-up, designed for students.

---

## Describe Azure physical infrastructure

**Azure Physical Infrastructure Overview:**

*Core Architectural Components:*

1. **Physical Infrastructure:**
   - Azure's backbone is formed by its physical infrastructure, analogous to large corporate datacenters.
   - At its foundation, Azure datacenters house computing resources organized in racks. Each datacenter is equipped with dedicated power, cooling, and networking infrastructure.

2. **Management Infrastructure:**
   - Complementing the physical setup, the management infrastructure includes a suite of tools and services for orchestrating and governing Azure resources.

*Physical Infrastructure Details:*

   - **Regions:**
     - Azure divides the globe into Regions, each representing a geographical area with one or multiple interconnected datacenters.
     - These datacenters within a region are networked with low-latency connectivity, allowing Azure to intelligently allocate and balance resources based on demand.
     - Choosing a specific region during resource deployment is a common practice, with certain services confined to specific regions.

   - **Availability Zones:**
     - To fortify resiliency, Azure implements Availability Zones within a region.
     - Each Availability Zone consists of physically distinct datacenters, each self-sufficient in power, cooling, and networking.
     - These zones serve as isolation boundaries; if one zone experiences disruptions, others continue functioning seamlessly.
     - A minimum of three availability zones is maintained for ensuring robustness.

   - **Region Pairs:**
     - Azure regions are paired strategically with another region within the same geographic proximity, separated by at least 300 miles.
     - This pairing mitigates the impact of unforeseen events like natural disasters, power outages, or civil unrest.
     - In the event of a regional outage, services automatically fail over to the paired region.

     - *Advantages:*
       - Priority restoration for at least one region during widespread outages.
       - Thoughtful rollout of planned updates to minimize downtime.
       - Data residency is maintained within the same geography for legal and jurisdictional adherence.
        ![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/55d71e23-07a4-48e1-8729-ccf1b89686c7)

   - **Sovereign Regions:**
     - Catering to compliance and legal requirements, Azure offers Sovereign Regions, isolated instances with restricted access.
     - Examples include US Gov Virginia, China East, etc.
     - These regions are operated by screened personnel and adhere to specific compliance certifications.

   - **Global Infrastructure Site:**
     - The Global infrastructure site provides an interactive platform for users to explore the foundational elements of Azure's infrastructure.

   - **Important Considerations:**
     - Availability Zones are not universally supported by all Azure services.
     - Manual configuration may be required for recovery and replication in certain scenarios.
     - Region pairing directions vary, with some regions paired in only one direction.

   - **Benefits of Azure Physical Infrastructure:**
     - Augmented resiliency and reliability, particularly beneficial for mission-critical workloads.
     - Geographic redundancy achieved through well-thought-out region pairs.
     - High-availability applications facilitated by strategically positioned Availability Zones.
     - Compliance options through dedicated sovereign regions.

Understanding the intricacies of Azure's physical infrastructure is pivotal for making informed decisions regarding resource deployment, ensuring the dependability of services, and adhering to specific compliance standards.

[Microsoft Datacenters](https://datacenters.microsoft.com/)
---

## Deep Dive into Azure Management Infrastructure

Azure's management infrastructure offers a layered approach to organizing your cloud resources. This structure ensures efficient billing, access control, and overall manageability, especially for complex deployments. Let's delve deeper into each component:

**1. Building Blocks: Azure Resources**

Imagine Azure resources as the individual bricks you use to build your cloud applications. These resources encompass a wide range, including virtual machines (VMs) for running applications, databases for storing data, cognitive services for adding intelligence to your apps, and much more. Each resource serves a specific purpose within your Azure solution.

**2. Grouping Resources: Resource Groups**

Think of resource groups as folders for your Azure resources. They provide a way to logically group related resources that work together. For example, you might create a resource group for your development environment, containing all the VMs, databases, and other resources needed for your developers. Resource groups offer several advantages:

* **Simplified Management:**  Apply actions (start, stop, delete) to the entire group instead of managing individual resources.
* **Access Control:** Grant or deny access to a group, affecting all resources within it.
* **Cost Tracking:** Track the combined cost of resources within a group for better budgeting.

**3. Management and Billing Boundaries: Azure Subscriptions**

Azure subscriptions act as containers for your resource groups. They represent a unit of management, billing, and scale. Here's what subscriptions bring to the table:

* **Management:** Organize your resources logically across different projects or departments.
* **Billing:** Define separate billing boundaries for different purposes. Each subscription receives its own bill, allowing you to track costs more granularly.
* **Access Control:** Apply access control policies at the subscription level, ensuring only authorized users can access resources within that subscription.

**Choosing the Right Subscription Model:**

* **Separate Environments:** Create dedicated subscriptions for development, testing, and production environments, isolating resources for each stage.
* **Organizational Structures:** Align subscriptions with your organizational structure. For instance, a subscription for the marketing department with specific resource limitations.
* **Billing Management:**  Separate subscriptions for predictable vs. unpredictable workloads to optimize billing based on usage patterns.

**4. Enterprise-Scale Management: Azure Management Groups (Optional)**

For managing a vast number of subscriptions across complex deployments, Azure offers management groups. Think of them as super-folders that organize multiple subscriptions. Here's how they empower large-scale governance:

* **Hierarchical Organization:** Nest subscriptions within management groups, creating a structured hierarchy for easier management.
* **Inheriting Policies:** Apply governance policies (security, compliance) at the management group level, automatically inheriting them by all subscriptions within the group. This simplifies policy enforcement across numerous resources.
* **Simplified Access Control:** Assign Azure RBAC roles at the management group level, granting users access to all resources within the group and its descendant subscriptions.

**Benefits of a Structured Approach:**

* **Organization:** Group related resources together for better visibility and control.
* **Access Control:** Define granular access permissions at different levels (resource group, subscription, management group).
* **Policy Management:** Apply policies consistently across large deployments for enhanced security and compliance.
* **Cost Optimization:** Track and manage costs effectively through separate billing boundaries for subscriptions.

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/63e7b74d-fe8d-461e-9c17-0a1ae0216378)


**Key Takeaways:**

* Utilize resource groups to manage and control logically related resources.
* Leverage subscriptions for billing boundaries, access control, and overall organization.
* Consider management groups for large-scale deployments requiring centralized governance.

By understanding this hierarchical structure, you can effectively organize, manage, and control your Azure resources, ensuring a well-structured and efficient cloud environment.


---

## Azure Resource Group Population with VM Creation - A Walkthrough


### Task 1: Create a virtual machine

1. **Create a Virtual Machine:**

   * Sign in to the Azure portal.
   * Navigate to "Create a resource" > "Compute" > "Virtual Machine" > "Create".
   * On the "Basics" tab, verify or enter the requested values for VM configuration (subscription, resource group name, VM name, region, etc.).
   * Set a custom password for the VM.
   * Leave other options with default values.
   * Review and confirm the creation process, including any associated costs (which won't be charged in the sandbox environment).
   * Click "Create" to start VM provisioning. Wait for deployment to complete.

2. **Verify Created Resources:**

   * Once deployment finishes, return to the Azure portal home screen.
   * Select "Resource groups".
   * Choose the resource group named "learn-67541749-1b1a-487b-a347-dc7a19b28ce1" (or similar name based on your sandbox environment).
   * This resource group contains a list of resources created during VM deployment. You'll typically find resources like:
      * Virtual machine (your created VM)
      * Storage account (for VM storage)
      * Virtual network (for VM networking)
      * Additional resources with similar names, grouped for association with the VM

**Key Takeaways:**

* When you create a virtual machine in Azure, Azure automatically provisions additional resources required for the VM to function.
* These associated resources are grouped in the same resource group as the VM by default, simplifying management and association.
* Resource names often follow a similar pattern to aid identification and association.

**Additional Notes:**

* The sandbox environment automatically cleans up resources upon completion of the module.
* In a personal subscription, remember to clean up unused resources to avoid unnecessary costs. You can delete resources individually or delete the entire resource group.

