# Azure Virtual Machine (VM)

Azure Virtual Machine is an Infrastructure as a Service (IaaS) offering that provides an on-demand virtual server in the cloud.

<img src="https://images.openai.com/static-rsc-4/aafi-nvoqs1Pv1GnSpJCEnhzUiORYrvAryGdeBc5aWV9YtCCow5I-rs_HbXp_OHp8XeYZMIvOAWMO-AWwIaJnxWtNBU55YMgeP-IC641gyLNUYdg5wFr-TrpaaTxZUSEzVbIf0J7DngkOfgdvROQaeXcYqkRn06afZ3anKm26RpMYxkuqns3E32ul4sj5voq?purpose=fullsize" alt="Azure VM" width="650" />

---

## 1. Definition

An Azure VM is a scalable compute resource where you can run Windows or Linux operating systems and install your own applications.

---

## 2. Key Features

1. Full OS-level control
2. Supports both Windows and Linux
3. Pay-as-you-go pricing
4. Vertical and horizontal scaling options
5. Integrates with Azure networking, storage, and security services

---

## 3. VM Architecture (Quick View)

```text
Physical Server (Azure Data Center)
    -> Hypervisor
    -> Virtual Machines
```

---

## 4. Steps to Create an Azure VM (Portal)

### Step 1: Create a Resource Group

1. Go to https://portal.azure.com
2. Open Resource Groups
3. Select Create
4. Enter subscription, resource group name, and region
5. Select Review + Create, then Create

### Step 2: Create Virtual Machine

1. Select Create a resource -> Virtual Machine
2. In Basics tab, provide:
  - Subscription
  - Resource Group
  - VM Name
  - Region
  - Image (Ubuntu/Windows)
  - Size (for example, B1s)

### Step 3: Configure Administrator Account

- Username
- Password or SSH key

### Step 4: Configure Inbound Ports

- SSH (22) for Linux
- RDP (3389) for Windows

### Step 5: Configure Disks and Networking

- Disk type: HDD/SSD
- VNet and Subnet
- Public IP (if internet access is needed)
- NSG rules

### Step 6: Review, Create, and Connect

1. Select Review + Create
2. Deploy the VM
3. Connect:

```bash
# Linux
ssh username@public-ip
```

Windows: use Remote Desktop (RDP).

---

## 5. Create VM Using Azure CLI

### Login

```bash
az login
```

### Create Resource Group

```bash
az group create --name myRG --location centralindia
```

### Create VM

```bash
az vm create \
  --resource-group myRG \
  --name myVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
```

### Open SSH Port

```bash
az vm open-port --port 22 --resource-group myRG --name myVM
```

---

## 6. Infrastructure as Code (Advanced)

You can automate VM deployment through:

- ARM Templates (JSON)
- Bicep

Example deployment command:

```bash
az deployment group create
```

---

## 7. Important Interview Concepts

### VM Sizes

- B-series: budget workloads
- D-series: general purpose workloads

### Scaling

- Vertical scaling: change VM size
- Horizontal scaling: use VM Scale Sets

### Availability

- Availability Set: protects against host failures
- Availability Zones: protects against data center failures

### Storage Types

- Standard HDD
- Standard SSD
- Premium SSD

### Security

- NSG for network filtering
- Prefer SSH keys over passwords
- Store secrets in Azure Key Vault

### Monitoring and Backup

- Azure Monitor for metrics/logs
- Azure Backup for recovery

---

## 8. Why Resource Group Matters

1. Logical container for VM and related resources
2. Better management and billing organization
3. Easy cleanup by deleting the group
4. Policy and RBAC management at group scope

---

## 9. Quick Summary Table

| Feature | Azure VM |
| --- | --- |
| Service Type | IaaS |
| Control | Full OS control |
| Access | SSH / RDP |
| Scaling | Manual and Auto (VMSS) |
| Use Cases | App hosting, testing, backend workloads |

---

## 10. One-Line Interview Answer

Azure VM is an IaaS service that gives a virtual server in the cloud with full OS control to run applications.

---

## 11. Correct Deployment Flow

```text
Create Resource Group -> Create VM -> Configure Networking -> Connect
```
