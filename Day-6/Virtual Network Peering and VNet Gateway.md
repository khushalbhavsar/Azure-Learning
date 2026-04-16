# 🔗 1️⃣ Virtual Network Peering


## ✅ Definition

**Virtual Network Peering** connects two Azure VNets so they can communicate **privately using Azure backbone network**.

---

## 🧠 Simple Understanding

👉 Peering = **Direct private connection between VNets**

---

## 🔑 Key Features

1. **Private communication (no internet)**
2. **Low latency & high speed 🔥**
3. **No encryption needed (already secure Azure backbone)**
4. Works:

   * Same region
   * Different regions (Global Peering)

---

## ⚙️ How It Works

```text
VNet1 ↔ VNet2 (via Azure backbone)
```

---

## 🚀 Use Cases

* Hub-Spoke architecture
* Multi-tier applications
* Microservices communication

---

## ⚠️ Important Points

1. ❌ No overlapping IP ranges
2. ❌ Non-transitive (A↔B, B↔C ≠ A↔C)
3. ✔ Fastest connectivity

---

# 🔐 2️⃣ VNet Gateway (VPN Gateway)


## ✅ Definition

**VNet Gateway** is a service that enables **secure, encrypted communication between Azure VNet and external networks** using VPN.

---

## 🧠 Simple Understanding

👉 Gateway = **Secure tunnel (VPN) to outside world**

---

## 🔑 Types of Connections

---

### 🌐 1. Site-to-Site (S2S)

* Office network ↔ Azure

---

### 💻 2. Point-to-Site (P2S)

* Laptop ↔ Azure

---

### 🔁 3. VNet-to-VNet

* Azure VNet ↔ Azure VNet (via VPN)

---

## ⚙️ How It Works

```text
On-Prem → Internet → VPN Tunnel → Azure Gateway → VNet
```

---

## ⚠️ Requirements

1. Dedicated subnet:

   ```
   GatewaySubnet
   ```
2. Public IP
3. Takes ~30–45 minutes to deploy

---

# ⚖️ VNet Peering vs VNet Gateway (Important 🔥)

| Feature    | VNet Peering  | VNet Gateway    |
| ---------- | ------------- | --------------- |
| Speed      | High ⚡        | Medium          |
| Cost       | Low           | Higher          |
| Encryption | No            | Yes (IPSec)     |
| Internet   | Not used      | Uses internet   |
| Use Case   | Azure ↔ Azure | Azure ↔ On-prem |

---

# 🧠 When to Use What?

---

## 👉 Use Peering when:

* Both VNets are in Azure
* Need high performance

---

## 👉 Use Gateway when:

* Connecting to:

  * On-prem network
  * External users
* Need secure VPN

---

# 🏗️ Real Architecture

```text
On-Prem → VPN Gateway → Hub VNet
                         ↓
                    Spoke VNets (via Peering)
```

---

# 🎯 Interview One-Liner

👉 **VNet Peering connects Azure VNets privately with high speed, while VNet Gateway provides secure VPN connectivity between Azure and external networks.**

---

# 🚀 Quick Revision

```text
Peering → Fast Azure-to-Azure  
Gateway → Secure VPN connection
```

---

Perfect 🔥 Let’s do this **end-to-end using Azure Portal (UI)**:
👉 **VNet Peering + VNet Gateway (VPN Gateway)** — step-by-step.

---

# 🔗 Part 1: Create Virtual Network Peering (Portal)

---

## 🟢 Step 1️⃣ Create Two VNets

👉 Go to **Virtual Network → + Create**

Create:

* **VNet1**

  * Address space → `10.0.0.0/16`
* **VNet2**

  * Address space → `10.1.0.0/16`

❗ Make sure IP ranges do **NOT overlap**

---

## 🟢 Step 2️⃣ Add Peering (VNet1 → VNet2)

1. Open **VNet1**
2. Go to **Peerings**
3. Click **+ Add**

---

## 🟢 Step 3️⃣ Configure Peering

Fill:

### 📌 This VNet

* Peering name → `VNet1-to-VNet2`

### 📌 Remote VNet

* Select → `VNet2`

---

### 🔑 Enable Options (Important 🔥)

* ✅ Allow virtual network access
* ✅ Allow forwarded traffic
* (Optional) Allow gateway transit

👉 Click **Add**

---

## 🟢 Step 4️⃣ Create Reverse Peering

👉 Repeat same steps:

* Go to **VNet2 → Peerings → Add**
* Connect back to **VNet1**

---

## 🎉 Done!

👉 Now both VNets can communicate using **private IP**

---

# 🔐 Part 2: Create VNet Gateway (VPN Gateway)

---

## 🟢 Step 1️⃣ Create Gateway Subnet

1. Go to **VNet**
2. Click **Subnets → + Subnet**

Fill:

* Name → `GatewaySubnet` ❗ (must exact name)
* Address → `10.0.255.0/27`

👉 Save

---

## 🟢 Step 2️⃣ Create Public IP

1. Search **Public IP Address**
2. Click **+ Create**

Fill:

* Name → `myGatewayIP`
* SKU → Standard

👉 Create

---

## 🟢 Step 3️⃣ Create Virtual Network Gateway

1. Search **Virtual Network Gateway**
2. Click **+ Create**

---

### 📌 Basics

* Name → `myVpnGateway`
* Region → Same as VNet
* Gateway Type → **VPN**
* VPN Type → **Route-based 🔥**
* SKU → `VpnGw1`

---

### 📌 Networking

* Virtual Network → `VNet1`
* Gateway Subnet → Auto-detected
* Public IP → `myGatewayIP`

---

👉 Click **Review + Create → Create**

⏳ Takes **30–45 minutes**

---

## 🟢 Step 4️⃣ Create Connection

👉 For Site-to-Site (Office → Azure)

---

### Create Local Network Gateway

1. Search **Local Network Gateway**
2. Click **+ Create**

Fill:

* Name → `onPremNetwork`
* IP → Your office public IP
* Address range → `192.168.1.0/24`

---

---

### Create VPN Connection

1. Open **Virtual Network Gateway**
2. Go to **Connections → + Add**

Fill:

* Name → `myConnection`
* Type → Site-to-Site
* Local Gateway → `onPremNetwork`
* Shared Key → `mySecretKey`

👉 Create

---

## 🎉 Done!

👉 Secure VPN tunnel established

---

# 🧠 Final Architecture

```text
On-Prem → VPN Gateway → VNet1
                          ↓
                    VNet2 (via Peering)
```

---

# ⚠️ Important Points

### Peering:

* No overlapping IP
* Fastest connection

### Gateway:

* Needs `GatewaySubnet`
* Takes time to deploy
* Uses encryption

---

# 🎯 Interview One-Liner

👉 **VNet Peering connects Azure VNets privately, while VNet Gateway enables secure VPN connectivity between Azure and external networks.**

---

# 🚀 Quick Flow

```text
Create VNets → Add Peering → Create GatewaySubnet → Create VPN Gateway → Configure Connection
```

---
