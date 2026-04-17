# Azure Disk Storage

## Overview

Azure Disk Storage is a block-level storage service used to store data for Virtual Machines, including the operating system, applications, and databases.

## Simple Understanding

- Disk Storage is the hard disk of your VM in the cloud.

## Types of Disks

### OS Disk

- Contains the operating system
- Created automatically with the VM

### Data Disk

- Extra storage attached to the VM
- Used for databases, applications, and files

### Temporary Disk

- Provided by Azure
- Not persistent, so data is lost after restart

## Performance Types

### Standard HDD

- Low cost
- Low performance
- Use for backup and archive

### Standard SSD

- Medium performance
- Use for web apps and dev/test

### Premium SSD

- High performance
- Low latency
- Use for production apps and databases

### Ultra Disk

- Very high IOPS and throughput
- Use for high-end databases

## Key Concepts

### IOPS

Number of read and write operations per second.

### Throughput

Amount of data transferred per second.

### Latency

Time taken to respond.

## Features

- Managed disks
- High availability
- Encryption by default
- Snapshots and backups
- Scaling support

## Use Cases

- Virtual Machines
- Databases such as MySQL and SQL Server
- High-performance applications
- Enterprise workloads

## Example

Web app VM mapping:

- OS Disk -> Ubuntu
- Data Disk -> Database storage

## Important Points

- Persistent storage keeps data after reboot
- Usually attached to one VM at a time
- Performance depends on disk type
- Faster than Blob, but usually more expensive

## Blob vs Disk

| Feature | Disk | Blob |
| --- | --- | --- |
| Type | Block storage | Object storage |
| Use | VM storage | Files and media |
| Access | Attached to VM | HTTP or HTTPS |
| Performance | High | Medium |

## Interview One-Liner

Azure Disk Storage provides high-performance block storage for Virtual Machines to store OS, applications, and data.

## Quick Memory Trick

```text
Disk = VM Hard Drive
```
