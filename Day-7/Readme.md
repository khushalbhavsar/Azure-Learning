# 🚀 Azure Infrastructure + Nginx Deployment (Using Azure Portal)

---

# 🟢 Part 1: Create Azure Infrastructure

---

## 1️⃣ Create Resource Group

1. Go to **Azure Portal**
2. Search **Resource Groups**
3. Click **+ Create**
4. Fill:

   * Subscription → Select
   * Resource Group Name → `myRG`
   * Region → `Central India`
5. Click **Review + Create → Create**

---

## 2️⃣ Create Virtual Network (VNet)

1. Search **Virtual Network**
2. Click **+ Create**

### Basics Tab:

* Name → `myVNet`
* Region → Same as RG
* Resource Group → `myRG`

### IP Address Tab:

* Address Space → `10.0.0.0/16`
* Subnet:

  * Name → `web-subnet`
  * Address → `10.0.1.0/24`

👉 Click **Review + Create → Create**

---

## 3️⃣ Enable Azure Bastion (Secure Access)

👉 Bastion allows SSH/RDP without exposing VM to internet

### Step A: Create Bastion Subnet

1. Go to your VNet → Subnets → + Subnet
2. Name → `AzureBastionSubnet`
3. Address → `10.0.2.0/24`
4. Save

---

### Step B: Create Bastion

1. Search **Bastion**
2. Click **+ Create**

Fill:

* Name → `myBastion`
* Region → Same
* VNet → `myVNet`
* Public IP → Click **Create new**

  * Name → `myBastionIP`

👉 Click **Review + Create → Create**

---

## 4️⃣ Enable Azure Firewall

### Step A: Create Firewall Subnet

1. Go to VNet → Subnets → + Subnet
2. Name → `AzureFirewallSubnet`
3. Address → `10.0.3.0/24`
4. Save

---

### Step B: Create Firewall

1. Search **Azure Firewall**
2. Click **+ Create**

Fill:

* Name → `myFirewall`
* Region → Same
* VNet → `myVNet`
* Public IP → Create new (`myFirewallIP`)

👉 Click **Review + Create → Create**

---

## 5️⃣ Create Firewall Policy

1. Search **Firewall Policy**
2. Click **+ Create**

Fill:

* Name → `myFirewallPolicy`
* Region → Same

👉 Click **Create**

---

## 6️⃣ Attach Policy to Firewall

1. Open **Azure Firewall**
2. Go to **Settings → Firewall Policy**
3. Select `myFirewallPolicy`
4. Save

---

# 🟢 Part 2: Create Virtual Machine

---

## 7️⃣ Create VM

1. Search **Virtual Machines**
2. Click **+ Create → Azure Virtual Machine**

### Basics:

* Name → `myVM`
* Image → Ubuntu
* Size → B1s
* Authentication → SSH / Password

### Networking:

* VNet → `myVNet`
* Subnet → `web-subnet`
* Public IP → (Optional if using Bastion)

👉 Click **Review + Create → Create**

---

# 🟢 Part 3: Install Nginx

---

## 8️⃣ Connect to VM

👉 Use **Bastion (recommended)**

1. Go to VM → Click **Connect → Bastion**
2. Enter username/password
3. Connect

---

## 9️⃣ Update System

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 🔟 Install Nginx

```bash
sudo apt install nginx -y
```

---

## 1️⃣1️⃣ Start Nginx

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 1️⃣2️⃣ Create HTML Page

```bash
sudo vim /var/www/html/index.html
```

Paste:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Azure Demo</title>
</head>
<body>
    <h1>I Learnt Azure Networking 🚀</h1>
</body>
</html>
```

---

## 1️⃣3️⃣ Restart Nginx

```bash
sudo systemctl restart nginx
```

---

# 🎉 Final Output

👉 Open browser:

```
http://<public-ip>
```

---

# 🧠 Final Architecture

```
User → Firewall → Bastion → VM (Nginx)
```

---

# 🎯 Quick Summary

```
RG → VNet → Bastion → Firewall → Policy → VM → Nginx
```

---

# ⚠️ Important Notes

* Bastion = secure login (no public SSH)
* Firewall = controls traffic
* NSG should allow HTTP (port 80)
* Keep backend private for security

---
