# Azure File Storage

## Overview

Azure File Storage is a fully managed file sharing service that lets you create shared file systems in the cloud, accessible through SMB for Windows and NFS for Linux.

## Simple Understanding

- File Storage is a shared folder or network drive for multiple VMs.

## Structure

```text
Storage Account
   ↓
File Share
   ↓
Directories
   ↓
Files
```

## Example

```text
Storage Account: mystorage
File Share: sharedfiles
File: report.pdf
```

## Key Features

- Shared access for multiple VMs
- SMB for Windows and NFS for Linux
- Managed service with no server maintenance
- Mountable like a local drive

## Use Cases

### Shared Storage

Multiple servers access the same files.

### Lift-and-Shift Applications

Move on-premises apps to the cloud without major changes.

### Backup and Storage

Store logs and reports.

### Dev/Test Environments

Share code and configuration files.

## Security Features

- RBAC
- Storage keys and SAS tokens
- Encryption by default
- Private endpoints

## Performance Tiers

| Tier | Use |
| --- | --- |
| Standard | General use |
| Premium | High performance |

## Real Example

Company setup:

- Web VM and App VM both need the same files
- Use File Storage and mount it as a shared drive

## Important Points

- Works like a traditional file system
- Can be mounted on multiple machines
- Not ideal for very high-performance databases
- Better for shared access than Blob Storage

## File vs Blob vs Disk

| Feature | File | Blob | Disk |
| --- | --- | --- | --- |
| Type | File system | Object | Block |
| Access | SMB/NFS | HTTP | Attached to VM |
| Use | Shared files | Media | VM storage |

## Interview One-Liner

Azure File Storage provides fully managed shared file systems in the cloud accessible through SMB and NFS for multiple machines.

## Quick Memory Trick

```text
File Storage = Shared Folder
```

