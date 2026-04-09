# ☁️ What are Azure Resources?

**Azure Resources** are **individual cloud components/services** that you create and use in Microsoft Azure to build solutions.

👉 Example: Virtual Machine, Database, Storage Account, etc.
👉 All resources run inside **regions → availability zones → data centers**

---

# 🧩 Azure Resource Hierarchy (Very Important)

<img src="https://images.openai.com/static-rsc-4/KeRE1ucgMV3ZzrqDmehcYWTUbO5uU42xmjfbEx7UoN4Y20UZkofq4sYXv8nM07utrE-0fiUcT2vqLdSkoDWvK9i6g4i5HyUAq8I0lovciqlSVWCDG2vnpdR-Rwbe2ATGZZKm_nDlwn486nb6TkUc3j4IResin3WA1LaPahCtNLZyTj9PfgMbl32IWSyAN1_f?purpose=fullsize" alt="Image" width="650" />

### 📌 Flow:

```
Tenant (Azure AD)
   ↓
Management Group
   ↓
Subscription
   ↓
Resource Group
   ↓
Resources
```

---

## 🔑 Explanation

### 1️⃣ Tenant

* Represents your organization in Azure
* Managed via **Azure Active Directory (Entra ID)**

---

### 2️⃣ Management Group

* Used to organize multiple subscriptions
* Apply policies & access control at scale

---

### 3️⃣ Subscription

* Billing + access boundary
* Each subscription can contain multiple resource groups

---

### 4️⃣ Resource Group

* Logical container for resources
* Resources inside share lifecycle (deploy/delete together)

---

### 5️⃣ Resources

* Actual services (VM, DB, Storage, etc.)

---

# 📦 Types of Azure Resources

## 🖥️ 1. Compute Resources

<img src="https://images.openai.com/static-rsc-4/IKj9dHke1J27-_v54-ZCKkNb7e9FFfyvU5D1LNpglh-5782MIlnkwQFf2fSubAlBgp8vMB8p5Jp5niIUwJGYScVxiLlYUmJY8_oanDbh5PQcCIHKkPxTROTjTuQut15o3hLCCzKbsnDQiXDGQLkwbsqeBKPKLpV_tXWLsKWmCeLEZL9jUslSB2SCdiCKqjHa?purpose=fullsize" alt="Image" width="650" />

Used to run applications

* Azure Virtual Machines
* Azure App Service
* Azure Kubernetes Service
* Azure Functions

---

## 💾 2. Storage Resources

<img src="https://images.openai.com/static-rsc-4/PM5DxYCs_5rK3myuJRkIDPshEUlh-h0gLcDc9llRvJmimiAUfhOumMIWalqiemMgYxNQJs7E2889EkeqrbWRm919fR-W5miyq2hljijwsjQHofHpX2eLuxSAfXFlrh8iEM82y2JHWWyJbfx68P-irw8EtyXX34zS8gregcVymE_IaexXWOM85zAeDze7lIj9?purpose=fullsize" alt="Image" width="650" />

Used to store data

* Azure Blob Storage
* Azure Disk Storage
* Azure File Storage

---

## 🌐 3. Networking Resources

<img src="https://images.openai.com/static-rsc-4/zTX4nIUta-aNNbyu1d0dDPmBViHrcCYHM4y9ZJ-H6NG8tj-RY0o-jvckc455Pml28VEU7rs_WFQfc3AuYVU0I9IMqn3IXCx0Px3Dg83UanVw71gzGEMRwkEMDPABcUDh2TaS03n9x0_MJpjTCm6oJzeBD1J1XUO0_WH0Qjai0oGWtvTWaZoA3hYbo7485U04?purpose=fullsize" alt="Image" width="650" />
Used for connectivity

* Azure Virtual Network
* Azure Load Balancer
* Azure Application Gateway

---

## 🗄️ 4. Database Resources

<img src="https://images.openai.com/static-rsc-4/ecgI_4k6kcjfa8GeBxDwJNleqhjgOf4IcSUGSAtf5biLJsm9OgsDLn9sb-VM2toXMI4P0-8qoxeN9smkZpnqld-HmqiisvA8XO9yk_PdXkLOryIl0Z_e--NHzFMfZ_m2NLG89x-pie-mzVGYQnfz3HmHjSP1tLcejNeszCyAFmJGLu3bPebpzNPG7n5BkQf6?purpose=fullsize" alt="Image" width="650" />

Used to manage structured/unstructured data

* Azure SQL Database
* Azure Cosmos DB

---

## 🔐 5. Security & Identity

<img src="https://images.openai.com/static-rsc-4/UwwW9OT-XY5PIe2lsit2jG6Elq9vncdHi0r-IPqUbA1hR2lJUoTtzYcHocITUFH7QVYvAvAR0uq80hPmadz7kYaNMXxri-JvVzd3gbGAxxkS6NHcxF0deiBXaRs3CmoT6RXUOlGQ2qSrnxDpFeLQG0CvBZqzngbfAsYjca6TNYHZAVNFvdB0MbNBmmYjtWgc?purpose=fullsize" alt="Image" width="650" />
Used for identity and security

* Azure Active Directory
* Azure Key Vault

---

## 📊 6. Monitoring & Management

<img src="https://images.openai.com/static-rsc-4/ki3NKT5M_o1jhpaQMzSuPUpmomlJpaCeGcBXoxpgGIj_mwtGXzKHEGElEZAq-1AFhnlpceZc1J1KOmC_1GKOn7CPEfixJ356mQYePHbpstzPgpI1R-boao2NoXRw3yEIF6j9WRAoYU7ID-1WHkTclXdEV79BVAbxAtJMA_XDOw2KGpoW6YfNhLWRs8ebaAgB?purpose=fullsize" alt="Image" width="650" />
Used for monitoring and governance

* Azure Monitor
* Azure DevOps
* Azure Resource Manager

---

# ⚡ Key Concepts (Must Know)

### 1. Resource Group Rules

1. A resource can exist in only one resource group
2. Resource groups can contain multiple resource types
3. Resources can be moved between groups (with limits)

---

### 2. Resource Deployment

* Done using:

  * Azure Portal
  * CLI
  * ARM Templates / Bicep

---

### 3. Resource Naming

* Must be unique for some services (like storage accounts)

---

### 4. Resource Location

* Each resource is deployed in a **region**

---

# 🎯 Interview One-Liner

👉 **Azure Resource = Any service you create in Azure (VM, DB, Storage, etc.) managed inside Resource Groups and Subscriptions**

---

# 🚀 Quick Revision (Super Important)

```
Tenant → Subscription → Resource Group → Resources
```

* Resource Group = Container
* Resource = Actual service

---

