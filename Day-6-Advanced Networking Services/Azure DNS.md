# 🌐 What is Azure DNS?


### ✅ Definition

**Azure DNS** is a hosting service for **DNS domains** that translates human-readable domain names (like `example.com`) into IP addresses of Azure resources.

---

# 🧠 Simple Understanding

👉 Azure DNS = **Phonebook of the internet**

---

# 🔄 How DNS Works

```text
User → Domain Name → DNS → IP Address → Server
```

👉 Example:
`www.myapp.com → 20.204.45.123`

---

# 🧩 Key Components

---

## 1️⃣ DNS Zone

* Container for DNS records
  👉 Example: `myapp.com`

---

## 2️⃣ DNS Records

| Record | Purpose                 |
| ------ | ----------------------- |
| A      | Domain → IPv4           |
| AAAA   | Domain → IPv6           |
| CNAME  | Alias to another domain |
| MX     | Mail server             |
| TXT    | Verification/security   |

---

## 3️⃣ Name Servers

* Azure provides DNS servers
* You must update them at domain registrar

---

# ⚙️ Types of Azure DNS

---

## 🌐 1. Public DNS

* For internet-facing domains
  👉 Example: `mywebsite.com`

---

## 🔒 2. Private DNS

* For internal VNet resolution
  👉 Example: `vm1.internal.local`

---

# 🚀 How It Works in Azure

```text
User → Azure DNS → Public IP → Azure Resource (VM/App)
```

---

# ⚡ Use Cases

1. Host domain names
2. Connect domain to VM / App
3. Internal communication (Private DNS)
4. Email configuration (MX records)

---

# 🔐 Security Features

1. RBAC access control
2. DNSSEC (domain security)
3. Private DNS for internal use

---

# 🏗️ Real Example

👉 Website hosting:

1. Create VM with public IP
2. Create DNS Zone → `myapp.com`
3. Add A record:

   ```
   www → Public IP
   ```
4. Open:

   ```
   www.myapp.com
   ```

---

# ⚠️ Important Points

1. DNS does NOT host website (only maps names)
2. Changes take time (TTL propagation)
3. Must update name servers at registrar

---

# 📊 Public vs Private DNS

| Feature | Public DNS | Private DNS        |
| ------- | ---------- | ------------------ |
| Access  | Internet   | Internal           |
| Use     | Websites   | VNet communication |

---

# 🎯 Interview One-Liner

👉 **Azure DNS is a service that maps domain names to IP addresses and manages DNS records for Azure resources.**

---

# 🚀 Quick Memory Trick

```text
DNS = Domain → IP
```

---

# 🌐 Create Azure DNS (DNS Zone + Record)

---

# 🟢 Part 1: Create DNS Zone

---

## Step 1️⃣ Go to Azure Portal

1. Open **portal.azure.com**
2. Search **DNS Zones**
3. Click **+ Create**

---

## Step 2️⃣ Basics Tab

### 📌 Project Details

* **Subscription** → Select
* **Resource Group** → `myRG`

---

### 📌 Instance Details

* **Name (Domain Name)** → `myapp.com`
* **Region** → Global (default)

👉 Click **Review + Create → Create**

---

# 🎉 DNS Zone Created

---

# 🟢 Part 2: Get Name Servers (Important 🔥)

---

## Step 3️⃣ Copy Name Servers

1. Open your DNS Zone (`myapp.com`)
2. Go to **Overview**
3. Copy:

   ```
   ns1-xx.azure-dns.com  
   ns2-xx.azure-dns.net  
   ns3-xx.azure-dns.org  
   ns4-xx.azure-dns.info
   ```

---

## Step 4️⃣ Update at Domain Registrar

👉 Go to where you bought domain:

* GoDaddy / Namecheap / etc

👉 Replace default name servers with Azure DNS name servers

⏳ Takes time (DNS propagation)

---

# 🟢 Part 3: Create DNS Record

---

## Step 5️⃣ Add Record Set

1. Go to DNS Zone
2. Click **+ Record Set**

---

## Example: A Record (Domain → IP)

### Fill:

* **Name** → `www`
* **Type** → A
* **IP Address** → `20.x.x.x` (your VM public IP)

👉 Click **Add**

---

# 🟢 Part 4: Test DNS

---

## Step 6️⃣ Open Browser

```text
http://www.myapp.com
```

👉 Should open your website 🎉

---

# 🧠 DNS Flow

```text
User → Domain (myapp.com)
     → Azure DNS
     → Public IP
     → Azure VM / App
```

---

# ⚠️ Important Points

1. DNS Zone = domain container
2. Must update name servers
3. DNS takes time (TTL)
4. A record → IP mapping

---

# 🔑 Common Record Types

| Type  | Use          |
| ----- | ------------ |
| A     | Domain → IP  |
| CNAME | Alias        |
| MX    | Email        |
| TXT   | Verification |

---

# 🎯 Interview One-Liner

👉 **Azure DNS is created by configuring a DNS zone, updating name servers, and adding records to map domain names to IP addresses.**

---

# 🚀 Quick Flow

```text
Create DNS Zone → Copy Name Servers → Update Registrar → Add Record → Access Domain
```

---
