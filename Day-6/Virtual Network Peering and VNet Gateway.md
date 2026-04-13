# 🔗 1️⃣ Virtual Network Peering

## ✅ Definition

**Virtual Network Peering** connects two Azure VNets so they can communicate **privately using Azure backbone network**.

## 🔑 Key Features

1. **Private communication (no internet)**
2. **Low latency & high speed**
3. Works **within region & across regions (Global Peering)**
4. No need for VPN

## 🧠 Types of Peering

* **Regional Peering** → Same region
* **Global Peering** → Different regions

## ⚡ Use Cases

* Hub-Spoke architecture
* Microservices communication
* Multi-region apps

## ⚠️ Important Points

1. No overlapping IP ranges
2. Peering is **non-transitive**
3. Traffic stays in Azure network

---

# 🔐 2️⃣ VNet Gateway (VPN Gateway)

## ✅ Definition

**VNet Gateway** is a service that enables **secure communication between Azure VNet and external networks** (on-premises or other VNets) using VPN.

👉 Usually called **VPN Gateway**

## 🔑 Types of Connections

### 1️⃣ Site-to-Site (S2S)

* Office network ↔ Azure VNet

### 2️⃣ Point-to-Site (P2S)

* Individual device ↔ Azure VNet

### 3️⃣ VNet-to-VNet

* Connect two VNets using VPN

## ⚡ Key Features

1. Encrypted communication
2. Secure tunneling (IPSec)
3. Works over internet

## ⚠️ Important Requirements

* Dedicated subnet called **GatewaySubnet**
* Public IP required
* Takes ~30–45 mins to deploy

---

# ⚖️ Peering vs VNet Gateway (Most Asked 🔥)

| Feature  | VNet Peering          | VNet Gateway    |
| -------- | --------------------- | --------------- |
| Speed    | High                  | Medium          |
| Cost     | Low                   | Higher          |
| Security | Private Azure network | Encrypted VPN   |
| Internet | Not used              | Uses internet   |
| Use Case | Azure ↔ Azure         | Azure ↔ On-prem |

---

# 🚀 Steps to Create VNet Peering

---

## 🟢 Method: Azure Portal

### 1️⃣ Create Two VNets

* VNet1 → `10.0.0.0/16`
* VNet2 → `10.1.0.0/16`

---

### 2️⃣ Go to VNet1

* Click **Peerings → Add**

---

### 3️⃣ Configure Peering

* Peering name → `VNet1-to-VNet2`
* Select VNet2
* Enable:

  * Allow virtual network access
  * Allow forwarded traffic

---

### 4️⃣ Create Reverse Peering

* Repeat from VNet2 → VNet1

---

### 5️⃣ Test Connection

* Ping VM in another VNet (private IP)

---

# 🚀 Steps to Create VNet Gateway (VPN Gateway)

---

## 🟢 Step 1️⃣ Create VNet

* Address space: `10.0.0.0/16`

---

## 🟢 Step 2️⃣ Create GatewaySubnet

* Name: **GatewaySubnet**
* Range: `10.0.255.0/27`

---

## 🟢 Step 3️⃣ Create Public IP

* Name: `gateway-ip`
* SKU: Standard

---

## 🟢 Step 4️⃣ Create Virtual Network Gateway

* Gateway type → VPN
* VPN type → Route-based
* SKU → VpnGw1
* Attach:

  * VNet
  * GatewaySubnet
  * Public IP

---

## 🟢 Step 5️⃣ Configure Connection

### For Site-to-Site:

* Add Local Network Gateway
* Enter on-prem IP
* Create connection

---

## 🟢 Step 6️⃣ Test VPN

* Verify connection status
* Ping internal resources

---

# 🎯 Interview One-Liner

👉 **VNet Peering connects Azure VNets privately with high speed, while VNet Gateway provides secure VPN connectivity between Azure and external networks.**

---

# 🚀 Quick Revision

```
Peering → Azure to Azure (fast)  
Gateway → Azure to outside (secure VPN)
```

---

# 🔥 Pro Tips (Very Important)

1. Use **Peering for performance**
2. Use **Gateway for hybrid setup**
3. Combine both in **Hub-Spoke architecture**
4. Always plan **IP ranges carefully**

---