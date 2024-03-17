In this module, you’ll be introduced to the compute and networking services of Azure. You’ll learn about three of the compute options (virtual machines, containers, and Azure functions). You’ll also learn about some of the networking features, such as Azure virtual networks, Azure DNS, and Azure ExpressRoute.

# Learning objectives
After completing this module, you’ll be able to:
1. Compare compute types, including container instances, virtual machines, and functions.
2. Describe virtual machine options, including virtual machines (VMs), virtual machine scale sets, virtual machine availability sets, and Azure Virtual Desktop.
3. Describe resources required for virtual machines.
4. Describe application hosting options, including Azure Web Apps, containers, and virtual machines.
5. Describe virtual networking, including the purpose of Azure Virtual Networks, Azure virtual subnets, peering, Azure DNS, VPN Gateway, and ExpressRoute.
6. Define public and private endpoints.

 ---

## Azure Virtual Machines

**Azure Virtual Machines (VMs)** provide cloud-based virtualized servers that offer Infrastructure as a Service (IaaS). They function similarly to physical computers, allowing for complete software customization. VMs are ideal for scenarios requiring:

* Full control over the operating system (OS).
* Ability to run custom software.
* Use of custom hosting configurations.

**Benefits of Azure VMs:**

* **Flexibility:** VMs offer virtualization without the need to purchase and maintain physical hardware.
* **Rapid Provisioning:** VMs can be created or deployed from pre-configured images within minutes. These images act as templates and may include an OS and other software. 

**Scaling VMs in Azure:**

* **Single VMs:** Suitable for testing, development, or minor tasks.
* **VM Scale Sets:** A collection of identical, load-balanced VMs that are managed as a single unit. They automatically manage identical VMs, handle load balancing, and scale up/down based on needs.
* **VM Availability Sets:** A logical grouping of two or more VMs within a single Azure region.Enhance resiliency by ensuring VMs are staggered during updates and have varied power/network connectivity, preventing outages from single failures.

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/83eb5016-037a-495d-9971-8d17ca68a967)

**Use Cases for Azure VMs:**

* **Testing and Development:** VMs allow for quick creation of diverse OS and application configurations. They can be easily deleted when no longer needed.
* **Cloud-Based Applications:** Running specific applications in the cloud can be more economical than traditional on-premises infrastructure. This is especially true for applications with fluctuating demand.
* **Datacenter Extension:** Organizations can extend their on-premises network by creating a virtual network in Azure and incorporating VMs. This facilitates running applications like SharePoint on Azure VMs instead of locally.
* **Disaster Recovery:** VMs offer a cost-effective IaaS disaster recovery solution. VMs running critical applications on Azure can be activated in the event of a primary datacenter failure and deactivated upon restoration. 
* **Cloud Migration (Lift and Shift):** VMs are well-suited for migrating from physical servers to the cloud. Physical server images can be created and hosted within VMs with minimal modifications. However, similar to physical servers, VMs require maintenance of the installed OS and software.

**VM Resources:**

When provisioning a VM, you can choose its associated resources, including:

* Size (determines purpose, number of cores, and RAM)
* Storage disks (HDDs, SSDs, etc.)
* Networking (virtual network, public IP address, and port configuration)

---

## Create an Azure VM with Nginx on Student Portal

**Nginx (pronounced Engine-X)**: 
1.In the real world, creating an Azure virtual machine (VM) and installing Nginx on it is like setting up your own dedicated computer in the cloud to run a website
2.  This is a free and open-source web server software. It acts like a gatekeeper, receiving requests from web browsers trying to access your website and delivering the website's files (like HTML, images) in response.
3. By creating a VM with Nginx, you're essentially creating the foundation for your website in a secure and scalable environment. You can now upload your website's files to the VM and configure Nginx to serve them to visitors.


**Requirements:**

* Azure student account with free credit
* Basic understanding of command line and SSH

**Steps:**

1. **Access Azure Portal:** Login to [https://azure.microsoft.com/en-us/get-started/azure-portal](https://azure.microsoft.com/en-us/get-started/azure-portal) using your student account.
2. **Create Virtual Machine:**
    * Search for "Virtual Machines" and click "Create" or "+ Add."
    * Configure options:
        * Resource group: Create a new one or choose an existing one.
        * VM name: Enter a unique name (e.g., my-student-vm).
        * Region: Select a region closest to you.
        * Image: Choose a Linux distribution like "Ubuntu Server 22.04 LTS."
        * Instance details: Select an appropriate VM size.
        * Management: Create a strong password or SSH key pair.
    * Review details and click "Create" to provision the VM.

3. **Connect to VM:**
    * Find the VM in the portal and note the public IP address.
    * This address allows you to access your VM from the internet.
    * Use an SSH client (like PuTTY for Windows) to connect using username "azureuser" and your password/SSH key.

4. **Install Nginx:**
    * Update package lists: `sudo apt update`
    * Install Nginx: `sudo apt install nginx`
    * Verify installation: Open a web browser and navigate to the VM's public IP address (e.g., http://<public_ip_address>). You should see the Nginx welcome page.

5. **Secure your VM (Optional):**
    * Consider opening only port 80 (HTTP) for basic web server access.

**Saving Credits:**

* Delete the VM after use to avoid ongoing charges.

**Additional Notes:**

* This is a basic setup. Refer to Azure documentation for advanced configurations and security best practices.
* Student credit may have limitations. Monitor usage to stay within free tier limits.

---

## Azure Virtual Desktop (AVD)

**What is it?**

* A cloud-based desktop and application virtualization service.
* Enables users to access a virtual Windows desktop from anywhere, on any device.
* Works across devices, operating systems, and with most modern web browsers.

**Benefits:**

* **Enhanced Security:**
    * Centralized management with Microsoft Entra ID.
    * Multi-factor authentication for secure logins.
    * Granular role-based access controls (RBACs) for data security.
    * Data and applications separate from local device, reducing data leakage risk.
    * Isolated user sessions in both single and multi-session environments.
* **Multi-session Windows 10/11:**
    * Utilize Windows 10 or 11 Enterprise multi-session for multiple users on a single VM.
    * Consistent user experience with broad application support compared to Windows Server-based options.

**Real-world analogy:**

Imagine having a personal workspace (desktop) set up in a secure, high-rise office building (Azure cloud). You can access this workspace from any device (laptop, tablet, etc.) as if you were physically present in the office. The office building (Azure) manages security (multi-factor authentication, access controls) and keeps your work (data & applications) separate from your personal device.  

**Additional Notes:**

* Consider this as an alternative to traditional physical desktops or laptops.
* Ideal for organizations requiring secure access to Windows desktops and applications from various devices. 

---

## Azure Containers: Lightweight and Agile Application Deployment

**Containers vs. Virtual Machines:**

* **Virtual Machines (VMs):** Offer a complete operating system environment for each application. While cost-effective compared to physical hardware, VMs are limited to one OS per machine.

* **Containers:** Provide a lightweight virtualization environment, allowing multiple containers to run on a single host (physical or virtual). Unlike VMs, containers don't manage their own OS, making them faster to start, stop, and scale. 

**Benefits of Containers:**

* **Lightweight:** Reduced resource footprint compared to VMs.
* **Scalability:** Easily scale containerized applications up or down based on demand.
* **Agility:** Quickly respond to changes by rapidly creating, deploying, and restarting containers.
* **Portability:** Containers run consistently across different environments.

**Popular Container Engine: Docker**

* Docker is a widely used container engine that Azure supports.

**Azure Container Services:**

There are three primary Azure services for container deployment:

1. **Azure Container Instances (ACI):**
    * Simplest and fastest way to run containers in Azure.
    * Pay-per-use model - ideal for short-lived or sporadic workloads.
    * No VM management required.

2. **Azure Container Apps:**
    * Similar to ACI, removes container management complexity.
    * Offers additional features like load balancing and scaling for increased elasticity.

3. **Azure Kubernetes Service (AKS):**
    * Container orchestration service for managing fleets of containers.
    * Simplifies deploying and managing complex containerized applications.

**Microservices Architecture with Containers:**

* Containers are well-suited for microservices architecture, where applications are broken down into smaller, independent services.
* Each service can be containerized, allowing for independent scaling, updating, and maintenance.

**Real-world Example:**

Imagine a website with a front-end, back-end, and storage components. Using containers:

* If the back-end experiences high traffic, you can easily scale it up without impacting other components.
* If needed, you can update the storage service or modify the front-end independently.

---
## Azure Functions: Serverless Code Execution

**What are Azure Functions?**

Azure Functions is an event-driven, serverless compute service. Unlike traditional approaches with VMs or containers that require constant resource allocation, Azure Functions only run your code when triggered by an event. This eliminates the need to manage and maintain servers or containers when your application is idle.

**Benefits of Azure Functions:**

* **Focus on Code, Not Infrastructure:**  Azure Functions handles server management, letting you focus on writing the code that implements your application logic.
* **Event-Driven Execution:** Code runs only in response to events like HTTP requests, timers, or messages from other Azure services. 
* **Automatic Scaling:** Azure Functions automatically scale up or down based on demand, optimizing resource usage and cost.
* **Pay-Per-Use Model:** You only pay for the time your code executes, reducing costs when your application is not actively processing requests.
* **Stateless or Stateful:** Functions can be stateless (default) or stateful (Durable Functions) to manage application state across invocations. 

**Ideal Use Cases:**

* Processing data triggered by events (e.g., image uploads, sensor data)
* Responding to HTTP requests (APIs)
* Running scheduled tasks
* Integrating with other Azure services

---

## Application Hosting Options on Azure

**Choosing the Right Hosting Solution:**

* **Virtual Machines (VMs):** Offer maximum control and flexibility for experienced users, allowing custom configuration of the hosting environment.
* **Containers:** Provide isolated and individually managed components for robust and efficient application deployment.

**Beyond VMs and Containers:**

Azure offers additional options catering to various application types:

* **Azure App Service:** A comprehensive platform for hosting web apps, APIs, background jobs, and mobile backends.

**Benefits of Azure App Service:**

* **Focus on Code, Not Infrastructure:**  Manage your application code while Azure handles infrastructure management.
* **Automatic Scaling and High Availability:** Ensures smooth operation under varying workloads and guarantees uptime.
* **Broad Language Support:** Supports diverse programming languages (.NET, .NET Core, Java, Ruby, Node.js, PHP, Python) for development flexibility.
* **Windows and Linux Compatibility:** Offers hosting options for both Windows and Linux environments.
* **Continuous Deployment:** Enables automated deployments from Git repositories like GitHub and Azure DevOps.

**Types of App Services:**

App Service accommodates various application styles:

* **Web Apps:** Host web applications using languages like ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP, or Python. Supports both Windows and Linux environments.
* **API Apps:** Build and host RESTful APIs using your preferred language and framework. Includes full Swagger support and Azure Marketplace publishing capabilities.
* **WebJobs:** Execute background tasks as part of your application logic using WebJobs. These can be programs or scripts triggered by schedules or events. Supported languages include .exe, Java, PHP, Python, Node.js, .cmd, .bat, PowerShell, and Bash.
* **Mobile Apps:** Create backends for iOS and Android applications using Mobile Apps. Features include cloud-based data storage, social authentication, push notifications, and custom back-end logic execution in C# or Node.js.

---

## Azure Virtual Networking: Connecting Your Cloud Resources

**What is it?**

Azure virtual networking provides a secure and isolated network environment for your Azure resources to communicate with each other, the internet, and even your on-premises network. It acts as an extension of your local network within the Azure cloud.

**Key Capabilities:**

* **Isolation and Segmentation:**
    * Create private virtual networks with custom IP address spaces.
    * Divide networks into subnets for further organization.
    * Control network access with built-in name resolution services.
* **Internet Communication:**
    * Define public endpoints with public IP addresses for external access.
    * Utilize public load balancers to distribute traffic across resources.
* **Communication between Azure Resources:**
    * Connect VMs, App Services, Kubernetes clusters, and more within virtual networks.
    * Securely connect resources using service endpoints for Azure SQL databases and storage.
* **On-premises Connectivity:**
    * Establish secure connections between your Azure resources and on-premises environment.
    * Options include point-to-site VPNs, site-to-site VPNs, and Azure ExpressRoute.
* **Route Network Traffic:**
    * Leverage default routing between subnets, virtual networks, and the internet.
    * Customize routing behavior with route tables and Border Gateway Protocol (BGP).
* **Filter Network Traffic:**
    * Implement network security groups to define allow/block rules based on IP addresses, ports, and protocols.
    * Deploy network virtual appliances (NVAs) for advanced network functionalities like firewalls or WAN optimization.
* **Connect Virtual Networks:**
    * Directly connect virtual networks using virtual network peering for private communication.
    * Create a global interconnected network across different Azure regions.
    * Control routing between networks with user-defined routes (UDRs).

---

<details>
  <summary> Exercise:- Configure Network Access to your Azure VM </summary>

## Configure Network Access to your Azure VM

This exercise guides you through configuring network access to your Azure VM to allow access to the web server running on port 80.

**Prerequisites:**

* An active Azure Sandbox subscription
* A virtual machine (VM) created in the previous exercise named `my-vm` with Nginx installed

**Steps:**

1. **Verify VM is Running:**
   - Use the `az vm list` command to check if your VM is still running. If it's not, you'll need to recreate it following the previous exercise.

2. **Get VM IP Address:**
   - Run the `az vm list-ip-addresses` command to retrieve the public IP address assigned to your VM. Store the output in a variable named `IPADDRESS`.

3. **Test Initial Web Server Access (Unsuccessful):**
   - Try accessing the web server's homepage using `curl` with the retrieved IP address and port 80:
     ```bash
     curl --connect-timeout 5 http://$IPADDRESS
     ```
   - You'll likely receive a "Connection timed out" message as the default security group restricts access to port 80.

4. **List Current Network Security Group (NSG) Rules:**
   - Use `az network nsg list` to identify the NSG associated with your VM (usually named `my-vmNSG`).
   - Then, use `az network nsg rule list` to view the existing rules within the NSG. You'll see a default rule allowing SSH access on port 22.

5. **Create a New NSG Rule for Port 80 Access:**
   - Run the `az network nsg rule create` command to create a new rule named `allow-http` that permits inbound traffic on port 80 (HTTP):
     ```bash
     az network nsg rule create \
       --resource-group "[sandbox resource group name]" \
       --nsg-name my-vmNSG \
       --name allow-http \
       --protocol tcp \
       --priority 100 \
       --destination-port-range 80 \
       --access Allow
     ```
   - Verify the updated rule list using `az network nsg rule list`. You should now see both the default SSH rule and the new `allow-http` rule.

6. **Test Web Server Access Again (Successful):**
   - Retry accessing the web server using the same `curl` command. This time, you should receive the welcome message displayed by your Nginx web server.
   - Alternatively, refresh the browser tab pointing to your VM's IP address. You should now see the web server's homepage.

**Explanation:**

- By default, Azure VMs restrict access to specific ports for security reasons.
- Network security groups (NSGs) define rules to allow or deny inbound and outbound network traffic.
- This exercise created a new rule within the VM's NSG to allow HTTP traffic on port 80, enabling access to the web server.

**Important Notes:**

- The sandbox environment cleans up resources upon module completion.
- In a production environment, manage resource lifecycles to avoid unnecessary costs.
- Consider creating reusable NSGs with predefined access rules for consistent network security configurations across multiple VMs.

</details>

---

## Azure Virtual Private Networks (VPNs) Explained

**What is a VPN?**

A VPN creates a secure tunnel over a public network (like the internet) to connect private networks. It encrypts data traveling between the networks, protecting it from unauthorized access.

**Benefits of Azure VPN Gateways:**

* **Connect to Azure from Anywhere:** Securely connect your on-premises data centers or individual devices to your Azure virtual networks.
* **Supported Connections:**
    * Site-to-site (VPN): Connect your on-premises network to Azure.
    * Point-to-site (VPN): Connect individual devices to Azure.
    * Network-to-network (VPN): Connect multiple Azure virtual networks.
* **Encryption:** All data transferred through the VPN tunnel is encrypted for enhanced security.
* **High Availability:**
    * **Active/Standby:** Automatic failover to a backup VPN gateway for minimal downtime during maintenance or disruptions.
    * **Active/Active (with BGP):** Distribute traffic across multiple VPN gateways for increased redundancy.
    * **ExpressRoute Failover:** Use VPN as a backup connection if your ExpressRoute connection experiences an outage.
    * **Zone-Redundant Gateways (availability zones):** Deploy gateways in separate zones for added protection against zone-level failures.

**VPN Gateway Types:**

* **Policy-based VPN:** Defines static IP addresses for traffic encryption through specific tunnels.
* **Route-based VPN (recommended):** Uses IP routing to determine the appropriate tunnel for each data packet. Preferred for on-premises connections due to better resilience.

**Choosing the Right VPN Gateway:**

* Use route-based VPN gateways for:
    * Connections between virtual networks
    * Point-to-site connections
    * Multisite connections
    * Coexistence with Azure ExpressRoute
    * High-availability scenarios

**Key Takeaways:**

* Azure VPN gateways provide secure connectivity between your on-premises networks and Azure virtual networks.
* Different VPN types and high-availability configurations cater to various connectivity needs and redundancy requirements.
---

## Azure ExpressRoute: Private Connections to the Cloud

**What is Azure ExpressRoute?**

Azure ExpressRoute establishes a private connection between your on-premises network and Microsoft cloud services, bypassing the public internet. It utilizes a dedicated circuit provided by a connectivity partner.

**Benefits:**

* **Reliability and Speed:** ExpressRoute offers more consistent performance with lower latency compared to internet connections.
* **Security:** Data travels over a private connection, reducing the risk of exposure on the public internet.
* **Global Reach:** Connect to Microsoft cloud services across all regions within a specific geographical area.
* **Dynamic Routing:** Border Gateway Protocol (BGP) enables efficient routing between your network and Azure resources.
* **Built-in Redundancy:** Redundant connections ensure high availability and minimize downtime risks.

**Connecting to Azure ExpressRoute:**

* **Connectivity Providers:** Partner with a connectivity provider to establish an ExpressRoute circuit.
* **Connectivity Models:** Choose from four models for connecting your network:
    * Co-location at a cloud exchange provider
    * Point-to-point Ethernet connection
    * Any-to-any connection for Wide Area Networks (WANs)
    * Direct connection to Microsoft's global network (ExpressRoute Direct)

**Additional Considerations:**

* **Global Reach:** Connect multiple ExpressRoute circuits to enable data exchange across geographically dispersed locations.
* **Security:** While ExpressRoute is private, some traffic (DNS queries, certificate checks) may still use the public internet. Implement additional security measures as needed.

**Use Cases:**

* Organizations with frequent and critical cloud interactions benefit from the reliability and security of ExpressRoute.
* Businesses with geographically distributed locations can leverage ExpressRoute Global Reach for private data exchange.

**In Summary:**

Azure ExpressRoute provides a secure, reliable, and high-performance connection to Microsoft cloud services for organizations with demanding cloud requirements.
---

## Azure DNS: Managing Your Domain Names in the Cloud

Azure DNS is a domain name system (DNS) hosting service offered by Microsoft Azure. It allows you to manage your domain names and DNS records within the Azure cloud infrastructure.

**Key Benefits:**

* **Reliability and Performance:**
    * Global network of DNS servers ensures fast response times and high availability.
    * Anycast networking automatically routes queries to the closest server for optimal performance.
* **Security:**
    * Built on Azure Resource Manager with features like role-based access control and activity logs.
    * Provides secure management of your domain names and records.
* **Ease of Use:**
    * Integrates seamlessly with other Azure services using the same credentials and billing.
    * Manageable through the Azure portal, PowerShell cmdlets, Azure CLI, REST API, and SDKs.
* **Customizable Virtual Networks:**
    * Host private DNS domains with custom names within your virtual networks.
* **Alias Records:**
    * Simplify management by pointing DNS records to Azure resources like public IP addresses, Traffic Manager profiles, or CDN endpoints.

**In essence:**

Azure DNS provides a reliable, secure, and user-friendly platform for managing your domain names and DNS records entirely within the Azure cloud environment.

**Additional Notes:**

* Azure DNS cannot be used to purchase domain names. You can acquire them through App Service domains or a third-party registrar and then host them in Azure DNS.
---
