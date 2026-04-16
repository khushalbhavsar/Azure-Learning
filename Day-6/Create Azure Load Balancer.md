# ⚖️ Create Azure Load Balancer

---

# 🟢 Step 1️⃣ Prerequisites

Before creating Load Balancer:

1. ✅ Create **Resource Group** (`myRG`)
2. ✅ Create **Virtual Network (VNet)**
3. ✅ Create **2 or more VMs** (for load balancing)
4. ✅ Ensure VMs are in **same VNet/subnet**

---

# 🟢 Step 2️⃣ Go to Load Balancer

1. Open **Azure Portal**
2. Search **Load Balancer**
3. Click **+ Create**

---

# 🟢 Step 3️⃣ Basics Tab

---

## 📌 Project Details

* Subscription → Select
* Resource Group → `myRG`

---

## 📌 Instance Details

* Name → `myLoadBalancer`
* Region → Same as VMs
* Type → **Public (for internet access)**
* SKU → **Standard (Recommended 🔥)**

---

# 🟢 Step 4️⃣ Frontend IP Configuration

---

## 📌 Public IP

* Click **Add new Public IP**
* Name → `myPublicIP`
* SKU → Standard

👉 This will be your **entry point**

---

# 🟢 Step 5️⃣ Backend Pool

---

## 📌 Add Backend Pool

1. Name → `backendPool`
2. Add:

   * VM NICs
   * Select your VMs

👉 These VMs receive traffic

---

# 🟢 Step 6️⃣ Health Probe (Very Important 🔥)

---

## 📌 Configure Probe

* Name → `healthProbe`
* Protocol → HTTP
* Port → 80
* Path → `/`

👉 Removes unhealthy VMs automatically

---

# 🟢 Step 7️⃣ Load Balancing Rule

---

## 📌 Create Rule

* Name → `httpRule`
* Frontend Port → 80
* Backend Port → 80
* Protocol → TCP
* Backend Pool → `backendPool`
* Health Probe → `healthProbe`

---

# 🟢 Step 8️⃣ NAT Rules (Optional)

👉 For SSH/RDP access

* Map:

  * Port 5001 → VM1 (22)
  * Port 5002 → VM2 (22)

---

# 🟢 Step 9️⃣ Review + Create

1. Click **Review + Create**
2. Validate
3. Click **Create**

---

# 🎉 Done!

👉 Access your app:

```text
http://<public-ip>
```

---

# 🧠 Traffic Flow

```text
User → Load Balancer → VM1 / VM2 → Response
```

---

# ⚠️ Important Points

1. Use **2+ VMs**
2. Open port 80 in NSG
3. Configure health probe
4. Use Standard SKU

---

# 🔐 Best Practices

* Use multiple availability zones
* Combine with VM Scale Sets
* Monitor health

---

# 🎯 Interview One-Liner

👉 **Azure Load Balancer is created by configuring frontend IP, backend pool, health probe, and load balancing rules to distribute traffic across VMs.**

---

# 🚀 Quick Flow

```text
Create LB → Add Frontend IP → Add Backend Pool → Add Probe → Add Rule → Deploy
```

---
