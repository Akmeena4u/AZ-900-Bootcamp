This module covers some of the authorization and authentication methods available with Azure.

# Learning objectives
By the end of this module, you will be able to:

1. Describe directory services in Azure, including Microsoft Entra ID and Microsoft Entra Domain Services
2. Describe authentication methods in Azure, including single sign-on (SSO), multifactor authentication (MFA), and passwordless
3. Describe external identities and guest access in Azure
4. Describe Microsoft Entra Conditional Access
5. Describe Azure Role Based Access Control (RBAC)
Describe the concept of Zero Trust
Describe the purpose of the defense in depth model
Describe the purpose of Microsoft Defender for Cloud

---
## Azure Active Directory Explained: Your Cloud Identity and Access Manager

Azure Active Directory (now Microsoft Entra ID) simplifies user access management for cloud and on-premises resources. Here's a breakdown of its key features and functionalities:

**What it Does:**

* **Authentication:** Verifies user identities for accessing applications and resources.
    * Offers features like self-service password reset, multi-factor authentication, and secure password management.
* **Single Sign-On (SSO):** Allows users to sign in once and access multiple applications with the same credentials.
* **Application Management:** Provides tools to manage cloud and on-premises applications, including:
    * Application Proxy for securely publishing on-premises apps to the cloud.
    * Integration with SaaS applications.
    * My Apps portal for users to easily access all their assigned applications.
* **Device Management:** Enables device registration and management through tools like Microsoft Intune.
    * Supports enforcing Conditional Access policies based on device identity.

**Who Uses It:**

* **IT Administrators:** Control access to applications and resources based on organizational policies.
* **App Developers:** Implement SSO functionality and leverage existing user credentials within their applications.
* **Users:** Manage their identities and perform actions like self-service password reset.
* **Existing Microsoft Cloud Subscribers:** Users of Microsoft 365, Office 365, Azure, and Dynamics CRM Online already utilize Microsoft Entra ID for authentication.

**Benefits of Using Microsoft Entra ID:**

* **Centralized Identity Management:** Manage all user identities in one place, simplifying administration.
* **Enhanced Security:** Features like multi-factor authentication and conditional access help protect against unauthorized access.
* **Improved User Experience:** Single sign-on eliminates the need to remember multiple passwords for different applications.
* **Reduced IT Costs:** Less overhead managing multiple identity systems, especially for hybrid cloud environments.

**Connecting On-Premises Active Directory:**

* Microsoft Entra ID can integrate with your existing on-premises Active Directory using Azure AD Connect.
* This synchronization ensures a consistent user experience across cloud and on-premises resources.
* Users can leverage features like SSO, multi-factor authentication, and self-service password reset across both environments.

**Microsoft Entra Domain Services:**

* Provides managed domain services in Azure, eliminating the need to manage your own domain controllers.
* Ideal for running legacy applications in Azure that require domain join, group policy, LDAP, or Kerberos/NTLM authentication.
* Offers a seamless lift-and-shift experience for migrating on-premises workloads to Azure.

**Key Takeaways:**

* Microsoft Entra ID is a comprehensive identity and access management solution for the cloud and hybrid environments.
* It offers features to streamline user access, enhance security, and simplify IT administration.
* By integrating with on-premises Active Directory and providing managed domain services, Microsoft Entra ID caters to various cloud adoption scenarios.
---

## Azure Authentication: Keeping Your Cloud Secure and Convenient

Azure offers various authentication methods to balance security and ease of access for your cloud resources. Let's explore some common options:

**1. Standard Passwords:**

* Traditional username and password combination.
* Simple to use but less secure, especially with weak passwords. 

**2. Single Sign-On (SSO):**

* Sign in once and access multiple applications with the same credentials.
* Improves convenience but security relies on the initial authentication method.

**3. Multifactor Authentication (MFA):**

* Adds an extra layer of security beyond passwords.
* Requires one or more additional factors like codes sent to your phone, fingerprint scans, or facial recognition.
* Makes it harder for attackers to gain access even if they steal your password.

**4. Passwordless Authentication:**

* Eliminates passwords altogether for a more convenient and secure experience.
* Relies on a combination of factors like:
    * **Something you have:** Your phone, a security key.
    * **Something you are:** Fingerprint, facial recognition.
    * **Something you know:** A PIN.

**Choosing the Right Method:**

* **Passwords:** Simple but less secure. Consider using strong passwords and a password manager.
* **SSO:** Improves convenience for users and simplifies access management.
* **MFA:** Highly recommended for additional security, especially for critical accounts.
* **Passwordless:** Most convenient and secure option, but may require user education and setup.

**Azure Authentication Options:**

* **Microsoft Entra MFA:** Provides multifactor authentication capabilities.
* **Windows Hello for Business:** Uses biometrics (fingerprint, facial recognition) for passwordless login on Windows devices.
* **Microsoft Authenticator App:** Turns your phone into a passwordless credential using push notifications and biometrics.
* **FIDO2 Security Keys:** Physical hardware tokens that replace passwords for a secure and standardized login experience.

**Remember:** Strong authentication is crucial for protecting your cloud resources. Consider a combination of methods based on your specific security needs and user convenience.
---

## Working with External Identities in Azure

Azure helps you securely collaborate with people outside your organization using **Microsoft Entra External Identities**. This includes partners, vendors, customers, and anyone who needs access to your resources.

**Key Concepts:**

* **External Identities:** People, devices, or services from outside your organization.
* **Bring Your Own Identity (BYOI):** External users sign in with their existing credentials (e.g., work email, social login).
* **Microsoft Entra ID/Azure AD B2C:** Manage access for external users while keeping your resources protected.


**Collaboration Options:**

* **Business-to-Business (B2B) Collaboration:**
    * Let external users access your Microsoft apps and enterprise applications using their preferred credentials.
    * They appear as guest users in your directory.
* **B2B Direct Connect:**
    * Establish a trust relationship with another Microsoft Entra organization for seamless collaboration.
    * Enables features like shared Teams channels where external users can collaborate within their own Teams environment.
    * These users won't be in your directory but are visible within the shared channel and Teams admin reports.
* **Business-to-Consumer (B2C):**
    * Use Azure AD B2C to manage identity and access for consumers or customers using your custom-developed apps or SaaS applications (excluding Microsoft apps).

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/3cc04b31-e423-44b5-ba16-041fba6effd0)
![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/23d7ec33-39b7-4c17-a88b-154814a51a62)



**Benefits:**

* **Simplified Collaboration:** Securely work with external partners and vendors using their existing identities.
* **Improved User Experience:** External users sign in with familiar credentials for a smooth experience.
* **Enhanced Security:** Maintain control over access to your resources through Microsoft Entra ID/Azure AD B2C.


**Getting Started:**

* Use Microsoft Entra ID's B2B feature to invite guest users from other organizations or social accounts (e.g., Microsoft accounts).
* Manage access for guest users through access reviews, ensuring they have the appropriate permissions.


**Remember:**

Microsoft Entra External Identities provides a secure and flexible way to collaborate with external users in your Azure environment.

---
## Azure Conditional Access: Smarter Security for Your Resources

**What it is:**

Conditional Access is a powerful tool in Microsoft Entra ID that allows you to set access controls based on various factors.  Imagine an ID check, but for your cloud resources!

**How it Works:**

* **Signals:** During sign-in, Conditional Access gathers information about the user, their device, and their location.
* **Decisions:** Based on these signals, Conditional Access decides to:
    * **Grant full access:** User is at a familiar location and using a trusted device.
    * **Request MFA:** User is at an unusual location or using an unknown device, requiring extra verification.
    * **Block access:** Sign-in attempt seems too risky (e.g., unknown user, suspicious location).
* **Enforcement:** Conditional Access carries out the decision, allowing access, prompting for MFA, or blocking access entirely.

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/0c2e987c-73e8-43d8-9bc0-1e44d74f6ace)

**Benefits:**

* **Enhanced Security:** Granular access control based on user context reduces the risk of unauthorized access.
* **Improved User Experience:** Streamlined access for trusted users while adding security checks for potentially risky situations.
* **Empowered Users:** Users can be productive from anywhere while maintaining strong security.

**Use Cases:**

* **MFA Based on Context:** Require MFA for admins or access from outside the corporate network.
* **App Access Control:** Limit which email applications can connect to your service.
* **Managed Device Access:** Ensure access only from devices meeting your security standards.
* **Blocking Untrusted Access:** Block sign-in attempts from suspicious locations or unknown devices.

**In Summary:**

Conditional Access provides a dynamic approach to securing your Azure resources, adapting security measures based on real-time user context. 

---

## Azure Role-Based Access Control (RBAC): Simplified Security Management

Azure RBAC simplifies access control for your cloud resources based on the principle of least privilege.

**The Problem:**

* Managing individual access permissions for large teams can be tedious.
* Balancing security and ease of access requires a strategic approach.

**Azure RBAC to the Rescue:**

* **Predefined Roles:** Assign common access permissions with built-in roles (e.g., Owner, Reader, Contributor).
* **Custom Roles:** Define specific permissions for unique needs.
* **Group Assignments:** Efficiently manage access by assigning roles to groups.

**How it Works:**

1. **Roles:** Define access permissions for specific tasks (e.g., read-only access, full control).
2. **Scopes:** Specify the resources a role applies to (e.g., subscription, resource group, individual resource).
3. **Assignments:** Grant access by assigning roles to users, groups, or service identities.

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/dcbbd1bd-02f4-4ff7-9e5b-08b692c3a32d)

**Key Points:**

* **Hierarchical:** Permissions at a parent scope (e.g., management group) are inherited by child scopes (e.g., subscriptions).
* **Enforcement:** Azure Resource Manager enforces RBAC during actions initiated against Azure resources.
* **Allow Model:** Assigned roles grant specific permissions within their scope.

**Benefits:**

* **Simplified Management:** Efficiently control access for large teams.
* **Improved Security:** Grant only the necessary permissions based on user roles.
* **Scalability:** Easily adapt permissions as your cloud environment grows.

**In Summary:**

Azure RBAC provides a granular and secure approach to access control, ensuring your cloud resources are protected while empowering users to perform their tasks effectively.

---

## Understanding the Zero Trust Security Model

The Zero Trust security model is a way of thinking about security that prioritizes constant verification and minimizes inherent trust.  Imagine it like always checking someone's ID, even if they claim to be familiar!

**Why Zero Trust?**

Traditional security models relied on a perimeter defense, assuming devices inside the network were safe. However, with mobile workforces, cloud resources, and the increasing sophistication of cyberattacks, this approach is no longer sufficient.

**Zero Trust Principles:**

* **Verify Explicitly:** Always authenticate and authorize users based on all available information, not just location within a network.
* **Least Privilege Access:** Grant only the minimum access permissions needed for users to perform their tasks (Just-In-Time and Just-Enough-Access).
* **Assume Breach:**  Minimize the potential damage if a breach occurs by segmenting access and verifying end-to-end encryption. Use security analytics to detect threats and improve defenses.

**Shifting from Traditional Security:**

Traditionally, organizations relied on a secure internal network where only approved devices could connect. Zero Trust flips this concept, requiring authentication for everyone regardless of location.

**Benefits of Zero Trust:**

* **Enhanced Security:**  Reduces the attack surface and minimizes damage from breaches.
* **Improved User Experience:** Enables secure access from anywhere for authorized users.
* **Increased Agility:** Adapts to the dynamic nature of modern IT environments.

**In Summary:**

Zero Trust is a proactive security approach that safeguards your resources in today's ever-evolving threat landscape. 
![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/7bcb4436-11b1-49f8-ae70-a6ea514dbecc)

---

## Defense-in-Depth: Layered Security for Your Data

Defense-in-Depth (DiD) is a cybersecurity strategy that uses multiple layers of security controls to safeguard your data. Imagine a castle with multiple walls and defenses; each layer in DiD adds another barrier to prevent unauthorized access.

**Why Use DiD?**

* No single security measure is foolproof. DiD provides redundancy in case one layer is breached.
* Slows down attackers, giving security teams time to react and prevent further damage.
* Provides valuable security insights from each layer that can be used to improve overall security posture.

**The Layers of Defense:**

Visualize these layers surrounding the core data you want to protect:

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/4db022aa-6022-4b6a-9ea0-0e438ae60e38)


1. **Physical Security:**
    * Safeguards physical access to data centers and computing hardware.
    * Prevents unauthorized physical access to equipment.

2. **Identity and Access:**
    * Ensures identities are secure and access is granted only to authorized users.
    * Uses strong authentication methods like multi-factor authentication (MFA).
    * Monitors and audits sign-in events and changes.

3. **Perimeter:**
    * Protects against network-based attacks like DDoS attacks.
    * Filters malicious traffic before it reaches your resources.
    * Uses firewalls to detect and alert on suspicious activity.

4. **Network:**
    * Limits communication between resources, reducing the attack surface.
    * Follows a "deny by default" approach, explicitly allowing only authorized connections.
    * Controls inbound and outbound internet traffic.
    * Secures connections to on-premises networks.

5. **Compute:**
    * Secures virtual machines and endpoints from malware and vulnerabilities.
    * Ensures systems are patched and up-to-date.
    * Restricts access to virtual machines.

6. **Application:**
    * Integrates security throughout the software development lifecycle.
    * Builds applications with security in mind to minimize vulnerabilities.
    * Stores sensitive data securely.

7. **Data:**
    * Controls access to stored data and ensures its confidentiality, integrity, and availability.
    * May involve regulatory compliance requirements depending on the data type.

**Benefits of DiD:**

* Enhanced security posture through multiple layers of protection.
* Improved resilience against cyberattacks.
* Faster detection and response to security incidents.

**Azure and DiD:**

Microsoft Azure provides security features and tools at every layer of the DiD model, helping you create a secure environment for your data and applications.


---

## Microsoft Defender for Cloud: Your Cloud Security Guardian

Defender for Cloud is a one-stop shop for managing security posture, threat protection, and vulnerability scanning across your cloud, on-premises, hybrid, and multi-cloud environments.

**Key Features:**

* **Unified Monitoring:** Gain visibility into your entire security landscape, including Azure, on-premises, AWS, and GCP environments.
* **Vulnerability Assessments:** Identify and prioritize security weaknesses in your VMs, container registries, and SQL servers.
* **Threat Protection:**  Detect and respond to security threats targeting your resources and workloads.
* **Security Posture Management (CSPM):**  Enforce best practices and compliance standards across your cloud environments.
* **Secure Score:**  Track your overall security posture with a quantified score based on implemented security recommendations.

**Deployment:**

* Native integration with Azure for effortless deployment on Azure resources.
* Automatic deployment of Log Analytics agents for data collection in hybrid and multi-cloud environments.
* Extension of Defender for Cloud plans and CSPM features to non-Azure machines using Azure Arc.

**Protection Areas:**

* **Azure PaaS Services:**  Detects threats targeting Azure App Service, SQL databases, storage accounts, and more.
* **Azure Data Services:**  Classifies data in Azure SQL, identifies vulnerabilities in Azure SQL and Storage, and recommends mitigation actions.
* **Networks:**  Limits exposure to brute-force attacks through just-in-time VM access and secure access policy enforcement.
* **Hybrid Environments:**  Extends protection to on-premises machines using Azure Arc and Defender for Cloud's enhanced security features.
* **Multi-Cloud Environments:**  Protects resources in AWS and GCP through CSPM features, threat detection for containers and servers, and asset inventory management.

**Key functionalities:**

* **Continuous Assessment:** Regularly scans for vulnerabilities in your compute, data, and infrastructure using integrated vulnerability assessment tools.
* **Security Policies:**  Enforces security best practices through customizable policies tailored to your environment.
* **Azure Security Benchmark:**  Provides a baseline for secure configuration standards.
* **Security Alerts:**  Generates alerts with details on detected threats and recommended remediation steps.
* **Advanced Threat Protection:**  Offers various protections like just-in-time VM access control and adaptive application controls.

**Benefits:**

* **Improved Security Posture:**  Proactive identification and mitigation of security risks.
* **Centralized Management:**  Streamlined security management across diverse environments.
* **Enhanced Visibility:**  Clear understanding of your overall security health.
* **Faster Threat Detection and Response:**  Efficient incident identification and resolution.

**In Summary:**

Defender for Cloud empowers you to secure your cloud journey by providing a comprehensive suite of tools for threat protection, vulnerability management, and continuous security monitoring.
---


