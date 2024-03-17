
This module introduces you to storage in Azure, including things such as different types of storage and how a distributed infrastructure can make your data more resilient.

# Learning objectives
Upon completion of this module, you will be able to:

Compare Azure storage services
Describe storage tiers
Describe redundancy options
Describe storage account options and storage types
Identify options for moving files, including AzCopy, Azure Storage Explorer, and Azure File Sync
Describe migration options, including Azure Migrate and Azure Data Box

---

## Azure Storage Accounts Explained

An Azure storage account is a central location for all your data storage needs in Microsoft's Azure cloud platform. It provides a unique naming space to access your data from anywhere globally using HTTP or HTTPS. Here are the key things to remember about storage accounts:

**Types of Storage Accounts:**

The type of storage account you choose determines what data services and redundancy options are available. Here's a breakdown of the common types:

* **Standard general-purpose v2 (most recommended):** Supports various data storage services like blobs, files, queues, and tables. Ideal for most Azure storage needs.
* **Premium block blobs:** Designed for high-performance scenarios involving frequent data updates or small objects.
* **Premium file shares:** Caters to enterprise applications requiring exceptional file share performance. Supports both SMB and NFS protocols.
* **Premium page blobs:** Optimized for storing and accessing large data blobs with predictable access patterns.  

**Storage Redundancy Options:**

Azure storage accounts offer various redundancy options to ensure data availability and protection in case of outages. These include:

* **Locally redundant storage (LRS):** Stores data within a single data center but replicates it within that location for basic redundancy.
* **Geo-redundant storage (GRS):** Creates copies of your data in a secondary location hundreds of miles away for disaster recovery purposes.
* **Read-access geo-redundant storage (RA-GRS):** Similar to GRS but offers read-only access to the secondary location's data.
* **Zone-redundant storage (ZRS):** Stores data across multiple availability zones within the same region for enhanced fault tolerance within a region.
* **Geo-zone-redundant storage (GZRS) and Read-access geo-zone-redundant storage (RA-GZRS):** Combine geo-redundancy with zone-redundancy for the highest level of data durability and availability.

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/daf1b107-260e-4345-b2fa-d9d7b203a1fe)


**Storage Account Endpoints:**

Each storage account has a unique name within Azure, forming a specific endpoint for accessing your data. This endpoint combines the storage account name with the Azure Storage service endpoint URL. 

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/00e28b41-5334-49f5-b14e-d3aa2d5bfac4)

**Remember:**

* Storage account names must be 3-24 characters long, containing only lowercase letters and numbers.
* Names must be unique within Azure to maintain a distinct namespace for your data.

By understanding storage account types, redundancy options, and endpoints, you can effectively manage your data storage needs in Microsoft Azure.


---

## Azure Storage Services Explained

Azure Storage offers a comprehensive suite of cloud storage solutions to cater to various data storage needs. Here's a breakdown of the key services:

**1. Azure Blob Storage:**

* Designed for storing massive amounts of unstructured data like text, binary files, and media.
* Ideal for serving images and documents, video streaming, backups, and data archiving.
* Accessible from anywhere globally via HTTP(S). 
* Offers tiered storage options (hot, cool, cold, archive) to optimize costs based on data access frequency.

**2. Azure Files:**

* Provides fully managed file shares accessible through industry-standard SMB or NFS protocols.
* Seamless replacement for on-premises file shares with cloud-based accessibility.
* Enables concurrent mounting from cloud or on-premises deployments for Windows, Linux, and macOS clients.
* Offers shared access, simplified management, scripting support, resiliency, and familiar programmability for applications.

**3. Azure Queues:**

* Messaging service for storing large numbers of messages (up to 64KB each) for asynchronous processing.
* Accessible from anywhere worldwide over HTTP(S) for reliable message retrieval.
* Often used to create work backlogs for applications like processing uploaded forms or triggering actions.
* Integrates well with Azure Functions for triggered actions upon receiving messages.

**4. Azure Disks (Managed Disks):**

* Block-level storage volumes for Azure VMs, acting as virtual counterparts to physical disks.
* Managed by Azure for provisioning, maintenance, and resiliency, offering better availability than physical disks.
* Ideal for storing virtual machine data.

**5. Azure Tables (NoSQL):**

* Stores large amounts of structured, non-relational data.
* Accepts requests from within or outside the Azure cloud for hybrid/multi-cloud solutions.
* Well-suited for scenarios requiring non-relational data storage with high availability. 

**Benefits of Azure Storage:**

* Durable and highly available with redundancy options for disaster recovery.
* Secure with built-in encryption and access control mechanisms.
* Scalable to accommodate growing storage demands.
* Managed by Azure, reducing administrative overhead.
* Accessible from anywhere over HTTP(S) with client libraries and APIs for various programming languages.

By understanding these services and their functionalities, you can effectively choose the right Azure storage solution for your specific data storage requirements.

---

<details>
  <summary>Creating a Storage Blob in Azure</summary>
## Creating a Storage Blob in Azure

This exercise guides you through creating a storage account, container, and uploading a blob (file) to Azure storage. It also demonstrates changing blob access levels for web accessibility.

**Prerequisites:**

* Access to an Azure subscription (or a free Azure Sandbox account)

**Steps:**

1. **Create a Storage Account:**
   - Sign in to the Azure portal ([https://azure.microsoft.com/en-us/get-started/azure-portal](https://azure.microsoft.com/en-us/get-started/azure-portal)).
   - Search for "Create a resource".
   - Under "Categories", select "Storage".
   - Under "Storage accounts", select "Create".
   - Configure the following settings:
      * Resource group: Choose an existing resource group or create a new one.
      * Storage account name: Enter a unique name.
      * Location: Select a region.
      * Performance: Standard
      * Replication: Locally redundant storage (LRS) (for this exercise)
      * Allow enabling anonymous public access on containers: Checked (for this exercise)
   - Review and create the storage account.

2. **Work with Blob Storage:**
   - In the storage account, navigate to "Data storage" > "Containers".
   - Click "+ Container" to create a new container.
   - Provide a name for the container and set access level to "Private (no anonymous access)".
   - Create the container.

3. **Upload a Blob:**
   - In the container, select "Upload".
   - Browse and select an image file from your computer.
   - Upload the file.

4. **Accessing the Uploaded Blob (Initially Fails):**
   - Select the uploaded blob.
   - Copy the URL from the "URL" field and open it in a new browser tab.
   - You'll encounter an error message stating "The specified resource does not exist".

5. **Change Blob Access Level:**
   - Go back to the Azure portal.
   - Select the uploaded blob and choose "Change access level".
   - Set "Anonymous access level" to "Blob (anonymous read access for blobs only)".
   - Save the changes.

6. **Refresh the Web Access:**
   - Refresh the browser tab where you pasted the blob URL earlier.
   - You should now be able to access the uploaded image file through the web browser.

**Explanation:**

Initially, the uploaded blob has restricted access, preventing anonymous web viewing. By changing the access level to "Blob (anonymous read access for blobs only)", you grant read permissions for the specific blob, allowing it to be accessed directly using the URL.

**Important:**

Remember to set appropriate access levels for your blobs based on security requirements. Public access should only be enabled when necessary. 

</details>

---

## Moving Your Data to Azure: Choosing the Right Path

Migrating your data to the cloud can be a big step. Luckily, Azure offers two main options to fit your needs: Azure Migrate for online migrations and Azure Data Box for offline data transfers.

**Migrating While Staying Online with Azure Migrate**

Imagine a one-stop shop for your entire cloud migration journey. That's what Azure Migrate provides. It's a central hub that streamlines the process of assessing your on-premises data and seamlessly moving it to Azure. Here's what it offers:

* **Easy Management:** No need to juggle multiple tools. Azure Migrate acts as a command center, letting you track your progress and manage the entire migration process from start to finish.
* **Toolbox for Success:** Azure Migrate comes equipped with various tools to simplify each stage of migration:
    * **Discovery and Assessment:** This tool scans your on-premises servers (VMs, physical servers) to understand their migration readiness.
    * **Server Migration:** As the name suggests, this tool helps you migrate your VMs, physical servers, and even VMs from other clouds to Azure.
    * **Data Migration Assistant:** Specifically designed for SQL Servers, this tool identifies potential migration roadblocks and suggests solutions for a smooth transition.
    * **Database Migration Service:** This service takes care of migrating your on-premises databases to compatible Azure environments like Azure SQL Database or SQL Managed Instances.
    * **App Service Migration Assistant:** Moving websites? This tool analyzes your on-premises websites to ensure a seamless migration to Azure App Service.

**Going Offline with Azure Data Box**

What if you have a massive amount of data (think hundreds of terabytes) and limited internet bandwidth? Azure Data Box is your answer. It's a secure physical device that acts as a portable storage solution for offline data transfer to Azure.

* **Big Data, No Problem:** The Data Box boasts a high capacity of up to 80 TB, making it ideal for exceptionally large datasets that traditional network transfers would struggle with.
* **Security You Can Trust:** Data security is paramount. The Data Box utilizes a secure design and ships via a reliable carrier to ensure your data remains protected throughout the transfer process.
* **Simple Steps for Success:** Here's a simplified breakdown of using Azure Data Box:
    1. Order your Data Box through the Azure portal.
    2. Set up the device using a web interface and connect it to your network.
    3. Transfer your data to or from the Data Box depending on your migration needs.
    4. Once done, return the Data Box to Microsoft. For data import, the data upload to Azure happens automatically upon receiving the device.
    5. The entire process is tracked within the Azure portal, keeping you informed every step of the way.

**When to Choose Azure Data Box:**

* **Large One-Time Migrations:** Moving a huge amount of on-premises data to Azure in a single go.
* **Migrating Media Libraries:** Transferring offline media archives (like video or audio recordings) to Azure for online access and management.
* **Bulk Environment Migration:** Moving your entire IT infrastructure, including VMs, databases, and applications, to Azure at once.
* **Historical Data Analysis:** Transferring historical data for in-depth analysis and reporting using Azure HDInsight.
* **Regular Data Uploads:** Uploading large amounts of data that are generated on a regular basis to Azure.

**Beyond Migration: Additional Use Cases for Data Box**

Data Box offers more than just migration capabilities. Here are some additional scenarios where it can be valuable:

* **Disaster Recovery:** Create a backup copy of your Azure data by exporting it to an on-premises location using Data Box. This can be helpful in case of a disaster or outage in Azure.
* **Data Security and Compliance:** Certain regulations or security requirements might necessitate exporting data from Azure. Data Box facilitates this process securely.
* **Cloud Repatriation:** If you decide to move your data back from Azure to your on-premises environment or even to another cloud provider, Data Box can be used for secure data export.

**Remember:**

* Both Azure Migrate and Azure Data Box prioritize data security. Data Box devices are sanitized after data upload, adhering to strict security standards.

---

##  Azure File Movement Options: A Quick Guide

Moving files within Azure storage or between clouds can be done using various tools. Here's a simplified breakdown:

**1. AzCopy (for Automation Enthusiasts):**

* Prefers commands over clicks? AzCopy's your friend. It's a command-line tool for power users who like scripting and automating file transfers.
* Need to upload, download, or copy files between storage accounts? AzCopy can handle it.
* Want to move files in one direction (think copying to a backup)? AzCopy offers synchronization functionality (but not two-way).
* Working with multiple clouds? AzCopy can even transfer files between Azure and other cloud providers. 

**2. Azure Storage Explorer (for the Graphical User):**

* Prefer a visual interface for managing your files? Azure Storage Explorer is the way to go. It provides a user-friendly interface for interacting with files and blobs in your Azure storage account.
* Available on Windows, macOS, and Linux, it offers a familiar experience across different operating systems.
* Just like AzCopy, it lets you upload, download, and move files between storage accounts.
* Behind the scenes, Storage Explorer uses AzCopy to perform the actual file transfers.

**3. Azure File Sync (for Centralized Storage):**

* Want to centralize your file shares in Azure while keeping the feel of an on-premises server? Azure File Sync is your answer.
* It acts like a bridge, keeping your files bi-directionally synchronized between Azure and your on-premises storage.
* Access your data locally using familiar protocols like SMB, NFS, and FTPS, ensuring a smooth transition.
* Azure File Sync goes a step further by offering global caching and cloud tiering. Frequently accessed files are stored locally for faster access, while less used ones are kept in Azure to optimize costs.

**Choosing the Right Tool:**

* Need automation and scripting? AzCopy is the way to go.
* Prefer a graphical interface for easy management? Choose Azure Storage Explorer.
* Looking for centralized storage with bi-directional sync and on-premises compatibility? Azure File Sync is your best bet.


---
