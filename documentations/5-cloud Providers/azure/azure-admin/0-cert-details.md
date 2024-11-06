# 🎓 Azure Administrator Associate Certification Guide

## 📑 Table of Contents

1. [👥 Manage Identities and Governance (20-25%)](#manage-identities-and-governance-2025)
   - [🔐 Administer Identity](#administer-identity)
   - [⚖️ Administer Governance and Compliance](#administer-governance-and-compliance)
   - [🛠️ Administer Azure Resources](#administer-azure-resources)
2. [💾 Implement and Manage Storage (15-20%)](#implement-and-manage-storage-1520)
   - [📦 Administer Azure Storage](#administer-azure-storage)
3. [💻 Deploy and Manage Azure Compute Resources (20-25%)](#deploy-and-manage-azure-compute-resources-2025)
   - [🖥️ Administer Azure Virtual Machines](#administer-azure-virtual-machines)
   - [☁️ Administer PaaS Compute Options](#administer-paas-compute-options)
4. [🌐 Implement and Maintain Virtual Networking (15-20%)](#implement-and-maintain-virtual-networking-1520)
   - [🌉 Administer Virtual Networking](#administer-virtual-networking)
   - [🔗 Administer Interconnectivity](#administer-interconnectivity)
   - [🚦 Administer Network Traffic](#administer-network-traffic)
5. [📊 Monitor and Maintain Azure Resources (10-15%)](#monitor-and-maintain-azure-resources-1015)
   - [🛡️ Administer Data Protection](#administer-data-protection)
   - [📈 Administer Monitoring](#administer-monitoring)
6. [📝 Notes](#notes)

## 👥 Manage Identities and Governance (20-25%)

This section focuses on managing user identities, ensuring governance compliance, and overseeing Azure resources to maintain a secure and efficient environment.

### 🔐 Administer Identity

- **Microsoft Entra ID**: Formerly known as Azure Active Directory (Azure AD), Microsoft Entra ID is now the cornerstone for identity and access management in Azure.
- **User and Group Management**: Create, manage, and secure user accounts and groups.
- **Authentication Methods**: Implement multi-factor authentication (MFA) and single sign-on (SSO) for enhanced security.
- **Role-Based Access Control (RBAC)**: Assign roles to users to control access to Azure resources.

### ⚖️ Administer Governance and Compliance

- **Azure Policy**: Define and enforce organizational standards and assess compliance at-scale.
- **Azure Blueprints**: Create repeatable sets of Azure resources that adhere to organizational standards.
- **Resource Locks**: Protect critical resources from accidental deletion or modification.
- **Compliance Standards**: Ensure adherence to industry-specific regulations and standards.

### 🛠️ Administer Azure Resources

- **Resource Management**: Deploy, manage, and monitor Azure resources using the Azure portal, CLI, or PowerShell.
- **Tags and Resource Groups**: Organize resources for easier management and billing.
- **Azure Resource Manager (ARM)**: Utilize ARM templates for infrastructure as code (IaC) deployments.
- **Cost Management**: Monitor and optimize Azure spending.

## 💾 Implement and Manage Storage (15-20%)

This section covers the implementation and management of Azure storage solutions to ensure data is stored securely and efficiently.

### 📦 Administer Azure Storage

- **Storage Accounts**: Create and configure storage accounts for different types of data.
- **Blob Storage**: Manage unstructured data such as documents and media files.
- **File Storage**: Implement shared storage for legacy applications using Azure Files.
- **Disk Storage**: Manage disks for Azure virtual machines, including premium and standard disks.
- **Storage Security**: Implement encryption, access keys, and shared access signatures (SAS) to secure data.

## 💻 Deploy and Manage Azure Compute Resources (20-25%)

Learn to deploy and manage various compute resources in Azure, including virtual machines and Platform as a Service (PaaS) options.

### 🖥️ Administer Azure Virtual Machines

- **VM Deployment**: Create and configure Azure VMs using the Azure portal, CLI, or PowerShell.
- **Scaling VMs**: Implement scaling strategies to handle workload changes.
- **VM Monitoring**: Use Azure Monitor to track VM performance and health.
- **Backup and Recovery**: Set up backup solutions and disaster recovery for VMs.

### ☁️ Administer PaaS Compute Options

- **App Services**: Deploy and manage web apps, mobile app backends, and RESTful APIs.
- **Azure Functions**: Implement serverless computing for event-driven applications.
- **Azure Kubernetes Service (AKS)**: Deploy and manage containerized applications using Kubernetes.
- **Azure Batch**: Run large-scale parallel and high-performance computing applications.

## 🌐 Implement and Maintain Virtual Networking (15-20%)

This section delves into setting up and maintaining virtual networks to ensure secure and efficient connectivity within Azure.

### 🌉 Administer Virtual Networking

- **Virtual Networks (VNet)**: Create and manage VNets to securely connect Azure resources.
- **Subnets**: Segment VNets into subnets for better organization and security.
- **Network Security Groups (NSGs)**: Control inbound and outbound traffic to resources.

### 🔗 Administer Interconnectivity

- **VPN Gateways**: Establish secure connections between on-premises networks and Azure.
- **ExpressRoute**: Implement private connections for higher reliability and faster speeds.
- **VNet Peering**: Connect VNets within the same or different Azure regions.

### 🚦 Administer Network Traffic

- **Load Balancing**: Distribute incoming traffic across multiple resources for high availability.
- **Traffic Manager**: Direct user traffic to the most appropriate endpoint based on routing methods.
- **Azure Firewall**: Implement a robust firewall solution to protect Azure resources.

## 📊 Monitor and Maintain Azure Resources (10-15%)

Ensure the health, performance, and security of your Azure environment through effective monitoring and maintenance practices.

### 🛡️ Administer Data Protection

- **Azure Backup**: Implement backup solutions to protect data against loss.
- **Azure Site Recovery**: Ensure business continuity by replicating workloads to a secondary location.
- **Data Encryption**: Use encryption at rest and in transit to secure data.

### 📈 Administer Monitoring

- **Azure Monitor**: Collect and analyze telemetry data to monitor resource performance.
- **Log Analytics**: Query and analyze log data for insights and troubleshooting.
- **Alerts and Notifications**: Set up alerts to proactively manage issues.

## 📝 Notes

- **Microsoft Entra ID**: Azure Active Directory has been rebranded to Microsoft Entra ID. Ensure you use the updated terminology in all services and documentation.
- **Service Naming Updates**: All Azure services previously containing "Azure AD" in their names now reference "Entra ID." For example, "Azure AD Connect" is now "Entra ID Connect."
