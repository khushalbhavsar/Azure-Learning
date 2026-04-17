# 💻 Azure CLI Cheat Sheet (Top Commands)

---

# 🔐 1️⃣ Authentication & Account

```bash
az login
az logout
az account show
az account list
az account set --subscription <id>
```

---

# 📁 2️⃣ Resource Group

```bash
az group create --name myRG --location centralindia
az group list
az group show --name myRG
az group delete --name myRG
```

---

# 🌐 3️⃣ Virtual Network (VNet)

```bash
az network vnet create --name myVNet --resource-group myRG --address-prefix 10.0.0.0/16
az network vnet list
az network vnet show --name myVNet --resource-group myRG
```

---

# 🔌 4️⃣ Subnet

```bash
az network vnet subnet create --vnet-name myVNet --name web-subnet --resource-group myRG --address-prefix 10.0.1.0/24
az network vnet subnet list --resource-group myRG --vnet-name myVNet
```

---

# 🖥️ 5️⃣ Virtual Machine (VM)

```bash
az vm create --name myVM --resource-group myRG --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
az vm list
az vm show --name myVM --resource-group myRG
az vm start --name myVM --resource-group myRG
az vm stop --name myVM --resource-group myRG
az vm delete --name myVM --resource-group myRG
```

---

# 🌍 6️⃣ Public IP

```bash
az network public-ip create --name myPublicIP --resource-group myRG
az network public-ip list
```

---

# 🔐 7️⃣ Network Security Group (NSG)

```bash
az network nsg create --name myNSG --resource-group myRG
az network nsg rule create --nsg-name myNSG --resource-group myRG --name allowHTTP --protocol Tcp --priority 100 --destination-port-range 80 --access Allow
```

---

# ⚖️ 8️⃣ Load Balancer

```bash
az network lb create --name myLB --resource-group myRG --frontend-ip-name myFrontEnd --backend-pool-name myBackEnd
az network lb list
```

---

# 🌐 9️⃣ Application Gateway

```bash
az network application-gateway create --name myAppGateway --resource-group myRG --location centralindia
```

---

# 🔥 🔟 Azure Firewall

```bash
az network firewall create --name myFirewall --resource-group myRG --location centralindia
az network firewall list
```

---

# 🔗 1️⃣1️⃣ VNet Peering

```bash
az network vnet peering create --name peer1 --resource-group myRG --vnet-name myVNet --remote-vnet otherVNet --allow-vnet-access
```

---

# 🔐 1️⃣2️⃣ VPN Gateway

```bash
az network vnet-gateway create --name myGateway --resource-group myRG --vnet myVNet --public-ip-address myIP --gateway-type Vpn --vpn-type RouteBased
```

---

# 💾 1️⃣3️⃣ Storage Account

```bash
az storage account create --name mystorage123 --resource-group myRG --location centralindia --sku Standard_LRS
az storage account list
```

---

# 📦 1️⃣4️⃣ Blob Storage

```bash
az storage container create --name mycontainer --account-name mystorage123
az storage blob upload --container-name mycontainer --file file.txt --name file.txt --account-name mystorage123
```

---

# 📁 1️⃣5️⃣ File Storage

```bash
az storage share create --name myshare --account-name mystorage123
```

---

# 📬 1️⃣6️⃣ Queue Storage

```bash
az storage queue create --name myqueue --account-name mystorage123
```

---

# 📊 1️⃣7️⃣ Table Storage

```bash
az storage table create --name mytable --account-name mystorage123
```

---

# 🌐 1️⃣8️⃣ DNS

```bash
az network dns zone create --name mydomain.com --resource-group myRG
az network dns record-set a add-record --zone-name mydomain.com --resource-group myRG --record-set-name www --ipv4-address 20.x.x.x
```

---

# 📊 1️⃣9️⃣ Monitoring

```bash
az monitor metrics list
az monitor activity-log list
```

---

# ⚙️ 2️⃣0️⃣ General Utilities

```bash
az help
az version
az configure
```

---

# 🧠 Quick Summary

```text
Login → RG → VNet → VM → Storage → Networking → Security → Monitoring
```

---

# 🎯 Interview One-Liner

👉 **Azure CLI provides command-based access to create, manage, and automate Azure resources efficiently.**

---
