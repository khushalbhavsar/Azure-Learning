# Day 8: Azure Storage

## 📚 Table of Contents

1. [Azure Blob Storage (Main Focus)](#1-azure-blob-storage-main-focus)
2. [Azure Storage Overview](#2-azure-storage-overview)
3. [Storage Account Fundamentals](#3-storage-account-fundamentals)
4. [Storage Types Comparison](#4-storage-types-comparison)
5. [Practical Implementation](#5-practical-implementation)
6. [Quick Revision](#6-quick-revision)

---

# 1. 🔥 AZURE BLOB STORAGE (Main Focus)

## Great choice! 🔥 **Blob Storage is one of the most important Azure services**
(Very common in interviews + real projects)

---

## 📦 What is Azure Blob Storage?

### ✅ Definition
**Azure Blob Storage** is an **object storage service** used to store large amounts of **unstructured data** such as images, videos, backups, and documents.

### 🧠 Simple Understanding
- **Blob Storage** = Google Drive / S3-like storage in Azure
- Stores files as **objects (blobs)**

---

## 🧩 Blob Storage Structure (Very Important 🔥)

```
Storage Account
     ↓
Container (like folder)
     ↓
Blob (actual file)
```

### 🔑 Real Example
```
Storage Account: mystorage
Container: images
Blob: photo.jpg
```

---

## 📦 Types of Blobs

### 1️⃣ Block Blob (Most Used 🔥)
- **Stores files like:**
  - Images
  - Videos
  - Documents
- **Used for:** uploads/downloads

### 2️⃣ Append Blob
- Data is added continuously
- **Used for:**
  - Logs
  - Monitoring

### 3️⃣ Page Blob
- **Used for:** Virtual machine disks
- Random read/write access

| Blob Type | Best For | Max Size |
|-----------|----------|----------|
| Block | Files, Images, Videos | 4.75 TB |
| Append | Logs, Continuous Data | 195 GB |
| Page | VM Disks | 8 TB |

---

## ⚙️ Blob Storage Access

### Access Methods
1. HTTP/HTTPS URL
2. SDK / API
3. Azure Portal
4. CLI

### Example URL Format
```
https://mystorage.blob.core.windows.net/images/photo.jpg
```

### Access Levels (Container Level)

| Level | Description | Who Can Access |
|-------|-------------|-----------------|
| Private | Only authorized users | Authenticated users only |
| Blob | Public read for files | Anyone via direct URL |
| Container | Public read for all | Anyone, can list blobs |

---

## 💡 Storage Tiers (Cost Optimization)

| Tier | Use Case | Cost | Availability |
|------|----------|------|--------------|
| Hot | Frequent access | High | 99.9% |
| Cool | Rare access | Medium | 99% |
| Archive | Very rare access | Low | 99% |

**Note:** Archive tier requires minimum 180-day retention

---

## 🔐 Security Features

1. **RBAC** - Role-based access control
2. **SAS Token** - Temporary time-bound access
3. **Encryption** - Default at rest & in transit
4. **Private Endpoints** - Private network access
5. **Access Keys** - Storage account authentication

---

## 🚀 Common Use Cases

1. Website images/videos
2. Backup & disaster recovery
3. Big data analytics storage
4. Static website hosting
5. Log storage
6. Archive & compliance

---

## 🏗️ Real Project Example

### E-commerce Application
- **Product images** → Blob Storage (Block Blob)
- **User uploads** → Blob Storage (Block Blob)
- **Backups** → Blob Storage (Archive Tier)
- **Logs** → Blob Storage (Append Blob)

---

## ⚠️ Important Points

| Point | Details |
|-------|---------|
| Scalability | Unlimited storage |
| Durability | 99.999999999% (11 nines) |
| Cost | Low (tier-based) |
| Global Access | Accessible worldwide |
| SLA | 99.9% uptime guarantee |

---

## 🎯 Interview One-Liner
**Azure Blob Storage is an object storage service used to store unstructured data like images, videos, and backups in containers within a storage account.**

---

## 🚀 Quick Memory Trick
```
Blob = File Storage (Object)
Container = Folder
Storage Account = Drive
```

---

# 2. 📊 AZURE STORAGE OVERVIEW

**Azure Storage** is a cloud service that provides scalable, secure, and durable storage for files, objects, disks, messages, and tables.

### Key Components
- General Purpose v2 (Most used)
- Blob Storage account (Blob-centric scenarios)
- Storage account names must be globally unique and lowercase

---

# 3. 🏗️ STORAGE ACCOUNT FUNDAMENTALS

### Storage Account Creation
All Azure storage services are created inside a **Storage Account**.

### Performance Tiers

| Tier | Use Case | Latency |
|------|----------|---------|
| Hot | Frequent access | Low |
| Cool | Less frequent access | Medium |
| Archive | Rare access | High |

### Redundancy Options

| Type | Description | Durability | Cost |
|------|-------------|-----------|------|
| LRS | Local Redundancy (one region) | 99.999999999% | Lowest |
| ZRS | Zone Redundancy (3 zones) | 99.9999999999% | Medium |
| GRS | Geo Redundancy (2 regions) | 99.99999999999999% | Higher |
| RA-GRS | Read Access Geo Redundancy | 99.99999999999999% | Highest |

### Security Features
- Encryption at rest and in transit
- Access keys and SAS tokens
- RBAC integration
- Private endpoints
- Service endpoints

---

# 4. 💾 STORAGE TYPES COMPARISON

## Quick Comparison

| Type | Data Type | Best Use | Example |
|------|-----------|----------|---------|
| **Blob** | Unstructured | Media, backups, files | Product images |
| **Disk** | VM storage | OS, databases | VM hard drive |
| **File** | Shared files | File sharing, SMB | Shared folder |
| **Queue** | Messages | Async tasks | Order processing |
| **Table** | NoSQL | Logs, metadata | User logs |

---

## Individual Storage Types

### 📦 Blob Storage
- **Use:** Images, videos, documents, backups
- **Type:** Unstructured data
- **Access:** HTTP/HTTPS
- **Scalability:** Unlimited

### 💾 Disk Storage
- **Use:** VM operating systems and data disks
- **Type:** Structured blocks
- **Access:** Attached to VM
- **Performance:** High IOPS

### 📁 File Storage
- **Use:** Shared network drives
- **Type:** Hierarchical file system
- **Access:** SMB protocol
- **Use Case:** Windows/Linux file sharing

### 📬 Queue Storage
- **Use:** Message queuing, async processing
- **Type:** Messages
- **Access:** HTTP/HTTPS
- **Use Case:** Decoupled applications

### 📊 Table Storage
- **Use:** NoSQL data, logs, metadata
- **Type:** Key-value pairs
- **Access:** REST API
- **Use Case:** Semi-structured data

---

# 5. 🛠️ PRACTICAL IMPLEMENTATION

## Part 1: Create Storage Account

### Step 1: Go to Azure Portal
- Open portal.azure.com
- Search: Storage Accounts → + Create

### Step 2: Fill Basics
| Field | Value |
|-------|-------|
| Resource Group | myRG |
| Storage Account Name | mystorage123 |
| Region | Central India |
| Performance | Standard |
| Redundancy | LRS |

Click **Review + Create** → **Create**

---

## Part 2: Create Blob Storage (Object Storage)

### Use Blob Storage for:
- Images
- Videos
- Backups

### Steps:
1. Go to Storage Account → Data Storage → **Containers**
2. Click **+ Container**
3. Enter details:
   - **Name:** `images`
   - **Access level:** Private / Blob
4. Click **Create**

### Upload a File:
- Open container → **Upload** → Select file → **Upload**

---

## Part 3: Create File Storage (File Share)

### Use File Storage for:
- Shared folders
- Team file sharing

### Steps:
1. Go to Storage Account → **File Shares**
2. Click **+ File Share**
3. Enter:
   - **Name:** `sharedfiles`
4. Click **Create**

### Upload a File:
- Open share → **Upload file**

---

## Part 4: Create Queue Storage

### Use Queue Storage for:
- Message queuing
- Async processing

### Steps:
1. Go to Storage Account → **Queues**
2. Click **+ Queue**
3. Enter:
   - **Name:** `orderqueue`
4. Click **Create**

### Add a Message:
- Open queue → **Add message** → Enter text → **OK**

---

## Part 5: Create Table Storage

### Use Table Storage for:
- NoSQL data
- Log storage

### Steps:
1. Go to Storage Account → **Tables**
2. Click **+ Table**
3. Enter:
   - **Name:** `users`
4. Click **Create**

### Add Data:
- Open table → **Add entity**
- Add **PartitionKey**
- Add **RowKey**
- Add **Properties**

---

## Part 6: Create Disk Storage (VM Disk)

### Note: Disk is created with the VM

### Steps:
1. Go to **Virtual Machines** → **+ Create**
2. Select:
   - **Image:** Ubuntu or Windows
3. Go to **Disks** tab
4. Choose:
   - **OS Disk type:** SSD or HDD
5. Click **Create VM**

### Add a Data Disk:
- Go to VM → **Disks** → **+ Add Data Disk** → **Save**

---

# 6. 📝 QUICK REVISION

## Storage Types Quick Reference

| Storage | Type | Use |
|---------|------|-----|
| Blob | Unstructured | Images, videos |
| File | Hierarchical | Shared folders |
| Disk | Block | VM storage |
| Queue | Message | Messages |
| Table | NoSQL | Data |

---

## Final Architecture Flow

```
Storage Account
  ├── Blob (Files/Images/Videos)
  ├── File (Shared Drives)
  ├── Queue (Messages)
  ├── Table (NoSQL Data)
  └── Disk (VM Storage)
```

---

## Quick Memory Tricks

```
Blob = File Storage (Object) = AWS S3
Disk = VM Hard Drive
File = Shared Folder (SMB)
Queue = Message Queue
Table = NoSQL Database
```

---

## Interview Checklist

✅ Blob Storage = Object storage for unstructured data
✅ Storage Account = Container for all storage services
✅ Access Levels = Private, Blob, Container
✅ Storage Tiers = Hot, Cool, Archive
✅ Redundancy = LRS, ZRS, GRS, RA-GRS
✅ Types = 5 different storage types with different use cases

---

## 🎯 Next Topics

- **Blob vs File Storage vs Disk** (Very important)
- **How to host static website using Blob Storage**
- **SAS Token and Security**
- **Storage Account Keys and Access**
