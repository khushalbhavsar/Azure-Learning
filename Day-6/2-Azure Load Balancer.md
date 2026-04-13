# ⚖️ What is Azure Load Balancer?

![Image](https://images.openai.com/static-rsc-4/pPkAySQtD6ICfrqPl4gdI8uqMkf7CjahhhXNrJVDepPz-MngC4i-KOfRYgw0AD6joMvqCbUzkHzTOVu4zFQ2wUx5GQPjErh3_CWqunPMVUq3tzLl1lR7xHPJlfjTX_bnARL-M-2ky1EEb4NadPuqS3KbF8ZZUK8ez9TsoPbhX_ULf8kR6iAj5wr8xNyR_2fr?purpose=fullsize)


### ✅ Definition

**Azure Load Balancer** is a Layer 4 (Transport layer) service that distributes incoming and outgoing network traffic across multiple virtual machines to ensure high availability and reliability.

---

# 🧠 Overview of the Diagram

👉 This architecture has **2 layers (tiers):**

1. **Web Tier (Frontend)**
2. **Business Tier (Backend)**

👉 And **2 Load Balancers:**

* 🌐 Public Load Balancer
* 🔒 Internal Load Balancer

---

# 🌐 1️⃣ Public Load Balancer (Frontend Entry)

### 📌 What it does:

* Accepts traffic from **internet users**
* Example: User opens website → request comes on **port 80 (HTTP)**

### 🔄 Flow:

```
User → Public Load Balancer → Web Tier VMs
```

### 🧠 Key Points:

1. Uses **Public IP**
2. Distributes traffic across multiple **Web VMs**
3. Ensures **high availability**
4. If one VM fails → others handle traffic

---

# 🖥️ 2️⃣ Web Tier (Frontend Layer)

### 📌 What it contains:

* Multiple **VMs running web servers (HTML, CSS, React, etc.)**

### 🧠 Role:

* Handles **user requests**
* Sends data to backend for processing

---

# 🔒 3️⃣ Internal Load Balancer (Backend)

### 📌 What it does:

* Distributes traffic **inside VNet**
* Not accessible from internet

### 🔄 Flow:

```
Web Tier → Internal Load Balancer → Business Tier VMs
```

### 🧠 Key Points:

1. Uses **Private IP**
2. Works only inside network
3. More secure
4. Used for backend communication

---

# ⚙️ 4️⃣ Business Tier (Backend Layer)

### 📌 What it contains:

* Backend services (APIs, logic, DB connection)

### 🧠 Role:

* Processes data
* Handles business logic
* Runs on **port 443 (HTTPS)**

---

# 🔄 Complete Request Flow (End-to-End)

```text
User (Internet)
   ↓
Public Load Balancer (Port 80)
   ↓
Web Tier VMs (Frontend)
   ↓
Internal Load Balancer (Port 443)
   ↓
Business Tier VMs (Backend)
   ↓
Response back to User
```

---

# 🔐 Why This Architecture is Used

### ✅ 1. Security

* Backend is **not exposed to internet**
* Only frontend is public

---

### ✅ 2. High Availability

* Multiple VMs + Load Balancer
* No single point of failure

---

### ✅ 3. Scalability

* Add more VMs in:

  * Web tier
  * Business tier

---

### ✅ 4. Separation of Concerns

* Frontend and backend are isolated

---

# ⚡ Real Example (Easy to Understand)

👉 Think like this:

* Public LB = **Main gate of society**
* Web Tier = **Reception**
* Internal LB = **Security checkpoint inside**
* Business Tier = **Private office (restricted access)**

---

# ⚖️ Types of Azure Load Balancer

---

# 🧩 1️⃣ Based on Exposure (Most Important)

---

## 🌐 1. Public Load Balancer

### ✅ Definition

Internet-facing load balancer that distributes traffic from **external users → Azure VMs**

---

### 🔑 Key Features

1. Uses **Public IP**
2. Accessible over internet
3. Used for web applications

---

### ⚙️ Traffic Flow

```
User (Internet) → Public IP → Load Balancer → VMs
```

---

### 📌 Use Cases

* Hosting websites
* APIs
* Public applications

---

### ⚠️ Important Points

* Requires NSG rules
* Exposes services to internet

---

## 🔒 2. Internal Load Balancer

### ✅ Definition

Private load balancer that distributes traffic **inside a VNet**

---

### 🔑 Key Features

1. Uses **Private IP**
2. Not accessible from internet
3. Used for internal communication

---

### ⚙️ Traffic Flow

```
App Server → Internal LB → Database Servers
```

---

### 📌 Use Cases

* Backend services
* Microservices
* Database layer

---

### ⚠️ Important Points

* Works only inside VNet
* More secure than public LB

---

# 🧩 2️⃣ Based on SKU (Important for Interviews 🔥)

---

## 🟡 3. Basic Load Balancer

### ✅ Definition

Entry-level load balancer with limited features

---

### 🔑 Features

1. Free or low cost
2. Limited scalability
3. No zone redundancy

---

### ⚠️ Limitations

* Not recommended for production
* No SLA (availability guarantee)

---

## 🟢 4. Standard Load Balancer (Recommended 🔥)

### ✅ Definition

Advanced, production-ready load balancer

---

### 🔑 Features

1. High availability (99.99% SLA)
2. Zone redundant
3. Better security (closed by default)
4. Supports large-scale apps

---

### ⚠️ Important Points

* NSG must explicitly allow traffic
* Slightly higher cost

---

# ⚖️ Public vs Internal (Quick Table)

| Feature  | Public LB   | Internal LB      |
| -------- | ----------- | ---------------- |
| Access   | Internet    | Private          |
| IP Type  | Public IP   | Private IP       |
| Use Case | Web apps    | Backend services |
| Security | Less secure | More secure      |

---

# ⚖️ Basic vs Standard (Quick Table)

| Feature     | Basic           | Standard          |
| ----------- | --------------- | ----------------- |
| SLA         | No              | Yes               |
| Scalability | Limited         | High              |
| Security    | Open by default | Secure by default |
| Zones       | Not supported   | Supported         |
| Use         | Testing         | Production        |

---

# 🧠 Final Classification (Easy to Remember)

```
Azure Load Balancer Types:

1. Based on Exposure:
   → Public
   → Internal

2. Based on SKU:
   → Basic
   → Standard
```

---

# 🎯 Interview One-Liner

👉 **Azure Load Balancer types include Public and Internal (based on exposure) and Basic and Standard (based on features and scalability).**

---

# 🚀 Pro Tip (Very Important 🔥)

👉 In real projects:

* Use **Public + Standard LB** → for frontend
* Use **Internal + Standard LB** → for backend

---

# ⚙️ How It Works (Flow)

```id="z2qz8o"
User → Public IP → Load Balancer → Backend Pool (VMs)
```

---

# 🚀 Steps to Create Azure Load Balancer

---

## 🟢 Step 1️⃣ Create Resource Group

```bash id="zkm41l"
az group create --name myRG --location centralindia
```

---

## 🟢 Step 2️⃣ Create Public IP

```bash id="f24b6g"
az network public-ip create \
  --resource-group myRG \
  --name myPublicIP \
  --sku Standard
```

---

## 🟢 Step 3️⃣ Create Load Balancer

```bash id="42h5py"
az network lb create \
  --resource-group myRG \
  --name myLoadBalancer \
  --sku Standard \
  --public-ip-address myPublicIP \
  --frontend-ip-name myFrontEnd \
  --backend-pool-name myBackEndPool
```

---

## 🟢 Step 4️⃣ Create Health Probe

```bash id="j7w8ux"
az network lb probe create \
  --resource-group myRG \
  --lb-name myLoadBalancer \
  --name myHealthProbe \
  --protocol tcp \
  --port 80
```

---

## 🟢 Step 5️⃣ Create Load Balancing Rule

```bash id="5h24gg"
az network lb rule create \
  --resource-group myRG \
  --lb-name myLoadBalancer \
  --name myRule \
  --protocol tcp \
  --frontend-port 80 \
  --backend-port 80 \
  --frontend-ip-name myFrontEnd \
  --backend-pool-name myBackEndPool \
  --probe-name myHealthProbe
```

---

## 🟢 Step 6️⃣ Add VMs to Backend Pool

```bash id="vl7tr6"
az network nic ip-config address-pool add \
  --address-pool myBackEndPool \
  --ip-config-name ipconfig1 \
  --nic-name myNic \
  --resource-group myRG \
  --lb-name myLoadBalancer
```

---

# 📊 Load Balancer vs Application Gateway

| Feature  | Load Balancer   | Application Gateway |
| -------- | --------------- | ------------------- |
| Layer    | L4              | L7                  |
| Protocol | TCP/UDP         | HTTP/HTTPS          |
| Use      | Network traffic | Web traffic         |
| Features | Basic routing   | URL routing, SSL    |

---

# 🔐 Best Practices

1. Use **Standard SKU**
2. Always configure **health probes**
3. Use **multiple VMs (backend pool)**
4. Combine with **VM Scale Sets**
5. Use **NSG for security**

---

# ⚠️ Common Mistakes

1. ❌ No health probe
2. ❌ Only one VM in backend
3. ❌ Wrong port mapping
4. ❌ Not opening NSG ports

---

# 🎯 Interview One-Liner

👉 **Azure Load Balancer distributes network traffic across multiple VMs at Layer 4 to ensure high availability and fault tolerance.**

---

# 🚀 Quick Revision

```id="y7yq9q"
Frontend IP → Load Balancer → Backend Pool → Health Probe → Rule
```

---

# 🔥 Real Use Case

👉 Hosting website:

* Load Balancer → distributes traffic
* Multiple VMs → handle requests
* If one VM fails → others continue

---
