# 💻 What is Azure CLI?

### ✅ Definition

**Azure CLI (Command Line Interface)** is a command-line tool used to **create, manage, and automate Azure resources** using commands.

---

# 🧠 Simple Understanding

👉 Azure CLI = **Control Azure using terminal instead of portal**

---

# ⚙️ Azure CLI Basics

---

## 🔹 Install Azure CLI

* Windows → MSI installer
* Mac/Linux → Package manager

# Install Azure CLI

### Installation Overview
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli

### Install on Windows
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli

### Install on Linux
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt

### Install on Mac
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-macos

---

## 🔹 Login to Azure

```bash
az login
```

👉 Opens browser → authenticate

---

## 🔹 Check Subscription

```bash
az account show
```

---

# 🧩 Azure CLI Structure (Important 🔥)

```bash
az <group> <subgroup> <command> --parameters
```

---

## 📌 Example

```bash
az group create --name myRG --location centralindia
```

👉 Breakdown:

* `group` → resource group
* `create` → action

---

# 🚀 Creating Resources Using Azure CLI

---

## 🟢 1️⃣ Create Resource Group

```bash
az group create \
  --name myRG \
  --location centralindia
```

---

## 🟢 2️⃣ Create Virtual Network

```bash
az network vnet create \
  --resource-group myRG \
  --name myVNet \
  --address-prefix 10.0.0.0/16 \
  --subnet-name web-subnet \
  --subnet-prefix 10.0.1.0/24
```

---

## 🟢 3️⃣ Create Virtual Machine

```bash
az vm create \
  --resource-group myRG \
  --name myVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
```

---

## 🟢 4️⃣ Open Port (HTTP)

```bash
az vm open-port \
  --port 80 \
  --resource-group myRG \
  --name myVM
```

---

## 🟢 5️⃣ Create Storage Account

```bash
az storage account create \
  --name demostorage6979 \
  --resource-group myRG \
  --location centralindia \
  --sku Standard_LRS
```

---

# ⚡ Advanced CLI Concepts

---

## 🔹 JSON Output

```bash
az vm list --output table
```

Options:

* json
* table
* yaml

---

## 🔹 Query Filtering

```bash
az vm list --query "[].name"
```

👉 Extract specific data

---

## 🔹 Automation (Scripts)

👉 Example Bash Script:

```bash
#!/bin/bash
az group create --name myRG --location centralindia
az vm create --resource-group myRG --name myVM --image UbuntuLTS
```

---

# 🔄 CLI vs Portal

| Feature    | CLI    | Portal       |
| ---------- | ------ | ------------ |
| Speed      | Fast ⚡ | Slow         |
| Automation | Yes    | No           |
| GUI        | No     | Yes          |
| DevOps     | Best   | Not suitable |

---

# 🚀 Use Cases (Very Important 🔥)

---

## 1️⃣ Infrastructure Automation

* Create resources quickly

---

## 2️⃣ DevOps Pipelines

* Used in CI/CD (GitHub Actions, Azure DevOps)

---

## 3️⃣ Bulk Operations

* Manage multiple resources

---

## 4️⃣ Scripting & Repeatability

* Same setup again & again

---

## 5️⃣ Troubleshooting

* Quick commands for debugging

---

# 🏗️ Real Example

👉 Deploy Web App:

```bash
az group create --name myRG --location centralindia
az vm create --resource-group myRG --name webVM --image UbuntuLTS
az vm open-port --port 80 --name webVM --resource-group myRG
```

---

# ⚠️ Important Points

1. Commands are **idempotent**
2. Use **scripts for automation**
3. Requires authentication (`az login`)
4. Works with **Azure Resource Manager (ARM)**

---

# 🎯 Interview One-Liner

👉 **Azure CLI is a command-line tool used to manage and automate Azure resources efficiently through scripts and commands.**

---

# 🚀 Quick Memory Trick

```text
CLI = Automation + Speed + DevOps
```
