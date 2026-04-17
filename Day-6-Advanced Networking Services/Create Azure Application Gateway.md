# 🌐 Create Azure Application Gateway (Step-by-Step)

---

# 🟢 Step 1️⃣ Prerequisites

Before creating App Gateway:

1. ✅ Create **Resource Group** (`myRG`)
2. ✅ Create **Virtual Network (VNet)**
3. ✅ Create **Dedicated Subnet**

   * Name: `appgw-subnet`
   * Example: `10.0.4.0/24`

👉 App Gateway **must be in its own subnet**

---

# 🟢 Step 2️⃣ Go to Application Gateway

1. Open **Azure Portal**
2. Search **Application Gateway**
3. Click **+ Create**

---

# 🟢 Step 3️⃣ Basics Tab

---

## 📌 Project Details

* Subscription → Select
* Resource Group → `myRG`

---

## 📌 Instance Details

* Name → `myAppGateway`
* Region → Same as VNet
* Tier → **WAF v2 (Recommended 🔥)**

---

## 📌 Autoscaling

* Enable autoscaling
* Min: 1
* Max: 2

---

# 🟢 Step 4️⃣ Frontend IP Configuration

---

## 📌 Public Access

* Choose **Public**
* Create new Public IP → `myAppGwIP`

---

# 🟢 Step 5️⃣ Backend Pool

---

## 📌 Add Backend

* Target type → IP / VM
* Add:

  * VM private IP
  * Or VM NIC

👉 Example:

* Web VM 1
* Web VM 2

---

# 🟢 Step 6️⃣ Routing Rules (Very Important 🔥)

---

## 📌 Listener

* Name → `listener1`
* Protocol → HTTP / HTTPS
* Port → 80 / 443

---

## 📌 Backend Settings

* Protocol → HTTP
* Port → 80

---

## 📌 Rule

* Connect:

  * Listener → Backend Pool

---

# 🟢 Step 7️⃣ Health Probe

👉 Optional but recommended

* Protocol → HTTP
* Path → `/`

---

# 🟢 Step 8️⃣ WAF Configuration

---

## 📌 Enable WAF

* Mode:

  * Detection (test)
  * Prevention (production 🔥)

---

## 📌 Rule Set

* OWASP (default)

---

# 🟢 Step 9️⃣ Review + Create

1. Click **Review + Create**
2. Validate
3. Click **Create**

⏳ Takes 5–10 minutes

---

# 🎉 Done!

👉 Access via:

```text
http://<public-ip>
```

---

# 🧠 Traffic Flow

```text
User → App Gateway → Backend VMs → Response
```

---

# ⚠️ Important Points

1. Must use **separate subnet**
2. Open backend port (80/443)
3. Use WAF_v2 for production
4. Configure health probes

---

# 🔐 Best Practices

* Use HTTPS
* Enable WAF (Prevention mode)
* Use autoscaling
* Combine with Firewall

---

# 🎯 Interview One-Liner

👉 **Application Gateway is created by configuring frontend IP, backend pool, routing rules, and enabling WAF for secure web traffic management.**

---

# 🚀 Quick Flow

```text
Create VNet → Create Subnet → Create App Gateway → Add Backend → Add Rules → Enable WAF
```

---
