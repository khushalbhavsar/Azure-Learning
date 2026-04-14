# Day 8: Azure Storage

## Topics

- [Blob Storage](Blob%20Storage%20(Object%20Storage).md)
- [Disk Storage](Disk%20Storage.md)
- [File Storage](File%20Storage.md)
- [Queue Storage](Queue%20Storage.md)
- [Table Storage](Table%20Storage.md)

---

## Azure Storage Overview

**Azure Storage** is a cloud service that provides scalable, secure, and durable storage for files, objects, disks, messages, and tables.

### Storage Account

All Azure storage services are created inside a **Storage Account**.

Key points:

- General Purpose v2 is the most used account type
- Blob Storage account is used for blob-centric scenarios
- Storage account names must be globally unique and lowercase

### Performance Tiers

| Tier | Use |
| --- | --- |
| Hot | Frequent access |
| Cool | Less frequent access |
| Archive | Rare access |

### Security Features

- Encryption at rest and in transit
- Access keys and SAS tokens
- RBAC integration
- Private endpoints

### Redundancy Options

| Type | Description |
| --- | --- |
| LRS | Local redundancy |
| ZRS | Zone redundancy |
| GRS | Geo redundancy |
| RA-GRS | Read access geo redundancy |

### Quick Comparison

| Type | Data | Use |
| --- | --- | --- |
| Blob | Unstructured | Media, backup |
| Disk | VM storage | OS, DB |
| File | Shared files | File sharing |
| Queue | Messages | Async tasks |
| Table | NoSQL | Logs, metadata |

### Real Project Example

E-commerce app:

- Images -> Blob Storage
- VM OS -> Disk Storage
- Shared files -> File Storage
- Order queue -> Queue Storage
- Logs -> Table Storage

### Interview One-Liner

Azure Storage provides scalable and secure storage solutions like Blob, Disk, File, Queue, and Table for different types of data and workloads.

---

## Part 1: Create Storage Account

### Step 1: Go to Azure Portal

- Open portal.azure.com
- Search Storage Accounts -> + Create

### Step 2: Fill Basics

- Resource Group -> `myRG`
- Storage Account Name -> `mystorage123`
- Region -> Central India
- Performance -> Standard
- Redundancy -> LRS

Click Review + Create -> Create.

### Storage Account Created

---

## Part 2: Create Blob Storage (Object Storage)

Use Blob Storage for images, videos, and backups.

### Blob Storage Steps

1. Go to Storage Account -> Data Storage -> Containers
2. Click + Container
3. Enter:
   - Name -> `images`
   - Access level -> Private / Blob
4. Click Create

To upload a file:

- Open container -> Upload -> Select file -> Upload

---

## Part 3: Create File Storage (File Share)

Use File Storage for shared folders.

### File Storage Steps

1. Go to Storage Account -> File Shares
2. Click + File Share
3. Enter:
   - Name -> `sharedfiles`
4. Click Create

To upload a file:

- Open share -> Upload file

---

## Part 4: Create Queue Storage

Use Queue Storage for message queue and async processing.

### Queue Storage Steps

1. Go to Storage Account -> Queues
2. Click + Queue
3. Enter:
   - Name -> `orderqueue`
4. Click Create

To add a message:

- Open queue -> Add message -> Enter text -> OK

---

## Part 5: Create Table Storage

Use Table Storage for NoSQL data.

### Table Storage Steps

1. Go to Storage Account -> Tables
2. Click + Table
3. Enter:
   - Name -> `users`
4. Click Create

To add data:

- Open table -> Add entity
- Add PartitionKey
- Add RowKey
- Add Properties

---

## Part 6: Create Disk Storage (VM Disk)

Disk is created with the VM.

### Disk Storage Steps

1. Go to Virtual Machines -> + Create
2. Select:
   - Image -> Ubuntu or Windows
3. Go to Disks tab
4. Choose:
   - OS Disk type -> SSD or HDD
5. Click Create VM

To add a Data Disk:

- Go to VM -> Disks -> + Add Data Disk -> Save

---

## Summary of Use

| Storage Type | Use |
| --- | --- |
| Blob | Images, videos |
| File | Shared folders |
| Disk | VM storage |
| Queue | Messages |
| Table | NoSQL data |

## Final Flow

```text
Storage Account
  -> Blob (Files)
  -> File (Shared)
  -> Queue (Messages)
  -> Table (NoSQL)
  -> Disk (VM)
```

## Quick Revision

```text
Blob -> Files
Disk -> VM
File -> Shared
Queue -> Messages
Table -> NoSQL
```
