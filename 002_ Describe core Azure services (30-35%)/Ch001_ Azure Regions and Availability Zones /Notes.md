# Cloud Infrastructure Components Explained

  <img width="413" alt="image" src="https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/c1982656-84c2-48db-9de4-71c985f1ed88">

  </hr>

## Data Center

**Definition:**
A data center is a physical facility that provides hosting for a group of networked servers. It includes its own power, cooling, and networking infrastructure to ensure the efficient operation of servers and other hardware.

## Region

**Definition:**
A region is a geographical area on the planet that encompasses one or more data centers. These data centers are connected with a low-latency network, usually less than 2 milliseconds. Choosing a specific region is essential when deploying services, and certain services may only be available in specific regions.

**Key Points:**
- Some services are global and not bound to a specific region.
- Azure has 50+ regions globally, including special government and partnered regions.

## Availability Zone

**Definition:**
An availability zone is a regional feature that involves grouping physically separate facilities to protect against data center failures. If one zone goes down, others continue working. Azure supports two types of services within availability zones: zonal services (e.g., Virtual Machines) and zone-redundant services (e.g., SQL, Storage). Not all regions support availability zones, and a supported region has three or more zones.

## Region Pair

**Definition:**
Each region is paired with another region, forming a region pair. These pairs are static and cannot be chosen by users. Region pairs are physically isolated, with at least 300 miles distance when possible. The purpose is to maintain data residency for disaster recovery. Some services have platform-provided replication, and planned updates are synchronized across the pairs.

**Examples:**
- Region Pair A: East US and West US
- Region Pair B: UK West and UK South

## Geographies

**Definition:**
A geography is a discrete market typically containing two or more regions. Geographies ensure data residency, sovereignty, resiliency, and compliance requirements are met. They are fault-tolerant to protect against region-wide failures. Geographies are broken up into areas such as Americas, Europe, Asia Pacific, and Middle East and Africa. Each region belongs to only one geography.

**Key Points:**
- Geographies play a crucial role in meeting compliance and data residency needs.
- They provide a framework for organizing and managing Azure resources on a global scale.
