# 🌐 Create Azure Virtual Network (Complete Steps)



# 🟢 Method 1: Azure Portal (Beginner Friendly)

## 0️⃣ Prerequisites

1. Azure account + subscription
2. Decide IP ranges (e.g., `10.0.0.0/16`)
3. Plan subnets (e.g., `10.0.1.0/24`, `10.0.2.0/24`)

## 1️⃣ Create Resource Group

1. Go to **Resource Groups → Create**
2. Fill:

   * Name → `myRG`
   * Region → (e.g., Central India)
3. Click **Create**

## 2️⃣ Go to Virtual Network

1. Search **Virtual Network** in Azure Portal
2. Click **Create**

## 3️⃣ Basics Tab

Fill:

* **Subscription** → Select
* **Resource Group** → `myRG`
* **Name** → `myVNet`
* **Region** → Same as RG

## 4️⃣ IP Addresses Tab (Very Important 🔥)

### Address Space:

* Example: `10.0.0.0/16`

### Add Subnet:

* Name → `web-subnet`
* Range → `10.0.1.0/24`

👉 You can add more:

* `app-subnet → 10.0.2.0/24`
* `db-subnet → 10.0.3.0/24`

## 5️⃣ Security Tab

* DDoS Protection → Optional
* Firewall → Optional

## 6️⃣ Tags (Optional)

* Key → `Environment`
* Value → `Dev`

## 7️⃣ Review + Create

* Validate configuration
* Click **Create**

## 🎉 Done!

👉 Your VNet is ready

---

# ⚙️ Method 2: Azure CLI (Important for DevOps)

## 🔹 Step 1: Login

```bash
az login
```

## 🔹 Step 2: Create Resource Group

```bash
az group create \
  --name myRG \
  --location centralindia
```

## 🔹 Step 3: Create VNet + Subnet

```bash
az network vnet create \
  --resource-group myRG \
  --name myVNet \
  --address-prefix 10.0.0.0/16 \
  --subnet-name web-subnet \
  --subnet-prefix 10.0.1.0/24
```

## 🔹 Step 4: Add Another Subnet

```bash
az network vnet subnet create \
  --resource-group myRG \
  --vnet-name myVNet \
  --name app-subnet \
  --address-prefix 10.0.2.0/24
```

---

# 🧠 Important Concepts (Must Know)

## 1️⃣ Address Space

👉 Total IP range of VNet
Example: `10.0.0.0/16`

## 2️⃣ Subnet

👉 Division of VNet

* Improves security
* Organizes resources

## 3️⃣ Region

👉 VNet is tied to one region

## 4️⃣ Private IP

👉 Used inside VNet

---

# ⚠️ Common Mistakes

1. ❌ Overlapping IP ranges
2. ❌ Very small subnet size
3. ❌ Not planning architecture
4. ❌ Mixing environments (Dev + Prod)

---

# 🔐 Best Practices

1. Plan IP ranges properly
2. Use multiple subnets
3. Apply NSG for security
4. Keep DB in private subnet
5. Use naming conventions

---

# 📊 Example Architecture

| Subnet     | Use      |
| ---------- | -------- |
| web-subnet | Frontend |
| app-subnet | Backend  |
| db-subnet  | Database |

---

# 🎯 Interview One-Liner

👉 **Azure Virtual Network is created by defining an address space and subnets within a resource group to enable secure communication between resources.**

---

# 🚀 Quick Revision

```
Create RG → Create VNet → Add Address Space → Add Subnet → Deploy
```

---

