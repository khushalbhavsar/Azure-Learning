# Day 3: Azure Resources

---

## Table of Contents

1. [What are Azure Resources?](#what-are-azure-resources)
2. [Azure Resource Hierarchy](#azure-resource-hierarchy)
3. [Types of Azure Resources](#types-of-azure-resources)
4. [Key Concepts](#key-concepts)
5. [Resource Deployment](#resource-deployment)
6. [Best Practices](#best-practices)

---

## What are Azure Resources?

**Azure Resources** are **individual cloud components/services** that you create and use in Microsoft Azure to build solutions.

**Examples:**
- Virtual Machine
- Database
- Storage Account
- Virtual Network
- App Service

👉 All resources run inside: **Regions → Availability Zones → Data Centers**

---

## Azure Resource Hierarchy

### Resource Hierarchy Flow

```
Tenant (Azure AD / Entra ID)
   ↓
Management Group
   ↓
Subscription
   ↓
Resource Group
   ↓
Resources
```

### Detailed Explanation

#### 1. Tenant
- Represents your organization in Azure
- Managed via **Azure Active Directory (Entra ID)**
- One tenant per organization

#### 2. Management Group
- Used to organize multiple subscriptions
- Apply policies & access control at scale
- Useful for enterprise-level management

#### 3. Subscription
- Billing + access boundary
- Each subscription can contain multiple resource groups
- Separate billing for each subscription

#### 4. Resource Group
- Logical container for resources
- Resources inside share lifecycle (deploy/delete together)
- All resources must be in a resource group
- Single region scope (but can contain resources from multiple regions)

#### 5. Resources
- Actual services (VM, DB, Storage, etc.)
- Deployed within resource groups

---

## Types of Azure Resources

### 1. 🖥️ Compute Resources

Used to run applications and workloads.

| Service | Purpose |
|---------|---------|
| Azure Virtual Machines | Run custom OS & applications |
| Azure App Service | Host web apps, mobile backends |
| Azure Kubernetes Service (AKS) | Container orchestration |
| Azure Functions | Serverless compute |
| Azure Container Instances | Run containers without VMs |

---

### 2. 💾 Storage Resources

Used to store and manage data.

| Service | Purpose |
|---------|---------|
| Azure Blob Storage | Unstructured data (files, images) |
| Azure Disk Storage | Persistent storage for VMs |
| Azure File Storage | File shares for VMs |
| Azure Table Storage | NoSQL table storage |
| Azure Queue Storage | Message queuing |

---

### 3. 🌐 Networking Resources

Used for connectivity and communication.

| Service | Purpose |
|---------|---------|
| Azure Virtual Network | Isolated network environment |
| Azure Load Balancer | Distribute traffic (L4) |
| Azure Application Gateway | Advanced load balancing (L7) |
| Azure VPN Gateway | Site-to-site connectivity |
| Azure CDN | Content delivery network |
| Azure Express Route | Private dedicated connection |

---

### 4. 🗄️ Database Resources

Used to manage structured and unstructured data.

| Service | Purpose |
|---------|---------|
| Azure SQL Database | Relational database (SQL Server) |
| Azure Cosmos DB | NoSQL, globally distributed |
| Azure Database for PostgreSQL | Open-source PostgreSQL |
| Azure Database for MySQL | Open-source MySQL |
| Azure Database for MariaDB | Open-source MariaDB |

---

### 5. 🔐 Security & Identity

Used for identity and security management.

| Service | Purpose |
|---------|---------|
| Azure Active Directory (Entra ID) | Identity & access management |
| Azure Key Vault | Secure secrets management |
| Azure Security Center | Security posture management |
| Azure DDoS Protection | DDoS attack protection |

---

### 6. 📊 Monitoring & Management

Used for monitoring, governance, and administration.

| Service | Purpose |
|---------|---------|
| Azure Monitor | Monitoring & analytics |
| Azure DevOps | CI/CD & project management |
| Azure Resource Manager | Infrastructure deployment & management |
| Azure Policy | Enforce organizational standards |
| Azure Cost Management | Track and optimize costs |

---

## Key Concepts

### Resource Group Rules

1. A resource can exist in **only one** resource group
2. Resource groups can contain **multiple resource types**
3. Resources can be **moved** between groups (with some limitations)
4. Resource groups have a **lifecycle** - deleting a group deletes all resources

### Resource Deployment Methods

| Method | Use Case |
|--------|----------|
| **Azure Portal** | Manual, UI-based deployment |
| **Azure CLI** | Script-based, cross-platform |
| **ARM Templates** | Infrastructure as Code (JSON) |
| **Bicep** | Infrastructure as Code (simpler than ARM) |
| **Terraform** | Multi-cloud IaC |

### Resource Naming

- Some services require **globally unique names** (e.g., storage accounts)
- Follow naming conventions for consistency
- Use tags for organization and cost tracking

### Resource Location

- Each resource is deployed in a **specific region**
- Some services have **global scope** (e.g., CDN, DNS)
- Choose region based on:
  - Proximity to users (latency)
  - Data residency requirements
  - Cost variations by region

---

## Best Practices

1. ✅ Organize resources into logical resource groups
2. ✅ Use consistent naming conventions
3. ✅ Tag resources for better organization and cost tracking
4. ✅ Follow the principle of least privilege for access control
5. ✅ Use managed identities for authentication
6. ✅ Enable monitoring and logging for all resources
7. ✅ Implement disaster recovery & backup strategies
8. ✅ Review and optimize costs regularly

---

## 🎯 Interview One-Liner

👉 **Azure Resources are individual cloud services organized within Resource Groups and Subscriptions, managed through a hierarchical structure for access control and billing.**

---

## 🧠 Quick Revision

```
Tenant → Subscription → Resource Group → Resources
```

**Key Takeaway:**
- **Resource Group** = Container for logical grouping
- **Resource** = Actual Azure service

---
