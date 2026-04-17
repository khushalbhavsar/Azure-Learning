# Azure Blob Storage

## Overview

Azure Blob Storage is an object storage service used to store large amounts of unstructured data such as images, videos, backups, and documents.

## Simple Understanding

- Blob Storage is like Google Drive or S3-style storage in Azure.
- It stores files as objects called blobs.

## Structure

```text
Storage Account
  ↓
Container
  ↓
Blob
```

## Example

```text
Storage Account: mystorage
Container: images
Blob: photo.jpg
```

## Types of Blobs

### Block Blob

- Stores images, videos, and documents
- Used for uploads and downloads

### Append Blob

- Data is added continuously
- Used for logs and monitoring

### Page Blob

- Used for virtual machine disks
- Supports random read and write access

## Access Methods

1. HTTP or HTTPS URL
2. SDK or API
3. Azure Portal
4. CLI

Example URL:

```text
https://mystorage.blob.core.windows.net/images/photo.jpg
```

## Access Levels

| Level | Description |
| --- | --- |
| Private | Only authorized users |
| Blob | Public read for files |
| Container | Public read for all |

## Storage Tiers

| Tier | Use |
| --- | --- |
| Hot | Frequent access |
| Cool | Rare access |
| Archive | Very rare access |

## Security Features

- RBAC
- SAS tokens
- Encryption by default
- Private endpoints

## Use Cases

- Website images and videos
- Backup and disaster recovery
- Big data storage
- Static website hosting
- Log storage

## Real Example

E-commerce app mapping:

- Product images -> Blob Storage
- User uploads -> Blob Storage
- Backups -> Blob Storage

## Important Points

- Unlimited scalability
- Highly durable
- Low cost with tier-based pricing
- Accessible globally

## Interview One-Liner

Azure Blob Storage is an object storage service used to store unstructured data like images, videos, and backups in containers.

## Quick Memory Trick

```text
Blob = Object file storage
Container = Folder
```

