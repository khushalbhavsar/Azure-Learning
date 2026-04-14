# 💽 What is Azure Disk Storage?

### ✅ Definition

**Azure Disk Storage** is a **block-level storage service** used to store data for Virtual Machines (VMs), such as the operating system, applications, and databases.

---

# 🧠 Simple Understanding

👉 Disk Storage = **Hard disk (HDD/SSD) of your VM in the cloud**

---

# 🧩 Types of Disks (Very Important 🔥)

---

## 1️⃣ OS Disk

* Contains **Operating System (Linux/Windows)**
* Created automatically with VM

---

## 2️⃣ Data Disk

* Extra storage attached to VM
* Used for:

  * Databases
  * Applications
  * Files

---

## 3️⃣ Temporary Disk

* Provided by Azure (not persistent ❌)
* Data lost after restart

---

# ⚡ Disk Performance Types

---

## 🟡 1. Standard HDD

* Low cost
* Low performance
  👉 Use: Backup, archive

---

## 🟠 2. Standard SSD

* Medium performance
  👉 Use: Web apps, dev/test

---

## 🟢 3. Premium SSD (Most Used 🔥)

* High performance
* Low latency
  👉 Use: Production apps, databases

---

## 🔴 4. Ultra Disk

* Very high IOPS & throughput
  👉 Use: High-end databases

---

# 📊 Key Concepts

---

## 🔹 IOPS

👉 Number of read/write operations per second

---

## 🔹 Throughput

👉 Amount of data transferred (MB/s)

---

## 🔹 Latency

👉 Time taken to respond

---

# 🔐 Features

1. Managed disks (Azure handles storage)
2. High availability
3. Encryption by default
4. Snapshots & backups
5. Scaling support

---

# 🚀 Use Cases

1. Virtual Machines (OS + apps)
2. Databases (MySQL, SQL Server)
3. High-performance applications
4. Enterprise workloads

---

# 🏗️ Example

👉 Web App VM:

* OS Disk → Ubuntu
* Data Disk → Database storage

---

# ⚠️ Important Points

1. Persistent storage (data stays after reboot)
2. Attached to one VM at a time (mostly)
3. Performance depends on disk type
4. More expensive than Blob (but faster)

---

# ⚖️ Blob vs Disk (Quick Difference)

| Feature     | Disk           | Blob           |
| ----------- | -------------- | -------------- |
| Type        | Block storage  | Object storage |
| Use         | VM storage     | Files/media    |
| Access      | Attached to VM | HTTP/HTTPS     |
| Performance | High           | Medium         |

---

# 🎯 Interview One-Liner

👉 **Azure Disk Storage provides high-performance block storage for Virtual Machines to store OS, applications, and data.**

---

# 🚀 Quick Memory Trick

```text id="8w3yhn"
Disk = VM Hard Drive 💽
```

---
