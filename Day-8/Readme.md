# 💾 What is Azure Storage?


### ✅ Definition

**Azure Storage** is a cloud service that provides **scalable, secure, and durable storage** for data such as files, objects, disks, messages, and tables.

---

# 🧩 Types of Azure Storage Services

---

## 📦 1️⃣ Blob Storage (Object Storage)

👉 Azure Blob Storage

### 🔹 What it is

* Stores **unstructured data** (images, videos, backups)

### 🔹 Features

* Highly scalable
* Accessible via HTTP/HTTPS
* Supports containers

### 🔹 Use Cases

* Website images/videos
* Backup & restore
* Big data storage

---

## 💽 2️⃣ Disk Storage

👉 Azure Disk Storage

### 🔹 What it is

* Storage for **Virtual Machines (VMs)**

### 🔹 Types

* Standard HDD
* Standard SSD
* Premium SSD

### 🔹 Use Cases

* OS disk for VM
* Database storage
* High-performance apps

---

## 📁 3️⃣ File Storage

👉 Azure File Storage

### 🔹 What it is

* Managed **file shares in cloud**

### 🔹 Features

* Access via SMB/NFS
* Shared across multiple VMs

### 🔹 Use Cases

* Shared folders
* Lift-and-shift apps
* Backup storage

---

## 📬 4️⃣ Queue Storage

👉 Azure Queue Storage

### 🔹 What it is

* Stores **messages between services**

### 🔹 Features

* Decouples applications
* Supports async processing

### 🔹 Use Cases

* Background jobs
* Order processing systems
* Microservices communication

---

## 📊 5️⃣ Table Storage

👉 Azure Table Storage

### 🔹 What it is

* NoSQL key-value storage

### 🔹 Features

* Schema-less
* Fast access

### 🔹 Use Cases

* Logs
* Metadata storage
* IoT data

---

# 🧠 Storage Account (Important 🔥)

👉 All storage services are created inside a **Storage Account**

### 🔑 Types:

* General Purpose v2 (most used)
* Blob Storage account

---

# ⚡ Performance Tiers

| Tier    | Use             |
| ------- | --------------- |
| Hot     | Frequent access |
| Cool    | Less frequent   |
| Archive | Rare access     |

---

# 🔐 Security Features

1. Encryption (at rest + in transit)
2. Access keys & SAS tokens
3. RBAC integration
4. Private endpoints

---

# 🌍 Redundancy Options

| Type   | Description      |
| ------ | ---------------- |
| LRS    | Local redundancy |
| ZRS    | Zone redundancy  |
| GRS    | Geo redundancy   |
| RA-GRS | Read access geo  |

---

# 📊 Quick Comparison

| Type  | Data         | Use            |
| ----- | ------------ | -------------- |
| Blob  | Unstructured | Media, backup  |
| Disk  | VM storage   | OS, DB         |
| File  | Shared files | File sharing   |
| Queue | Messages     | Async tasks    |
| Table | NoSQL        | Logs, metadata |

---

# 🎯 Real Project Example

👉 E-commerce App:

* Images → Blob Storage
* VM OS → Disk Storage
* Shared files → File Storage
* Order queue → Queue Storage
* Logs → Table Storage

---

# 🎯 Interview One-Liner

👉 **Azure Storage provides scalable and secure storage solutions like Blob, Disk, File, Queue, and Table for different types of data and workloads.**

---

# 🚀 Quick Revision

```text
Blob → Files  
Disk → VM  
File → Shared  
Queue → Messages  
Table → NoSQL  
```

---

