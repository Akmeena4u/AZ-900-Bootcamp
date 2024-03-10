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
