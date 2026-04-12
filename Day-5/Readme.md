# Day 5: Azure Networking

---

## Table of Contents

1. [Virtual Network (VNet)](#virtual-network-vnet)
2. [Subnets & CIDR](#subnets--cidr)
3. [IP Addressing](#ip-addressing)
4. [Routes & Route Tables](#routes--route-tables)
5. [Network Security Groups (NSGs)](#network-security-groups-nsgs)
6. [Application Security Groups (ASGs)](#application-security-groups-asgs)
7. [Communication Types](#communication-types)
8. [VNet Architecture](#vnet-architecture)
9. [Best Practices](#best-practices)

---

## Virtual Network (VNet)

### Definition

**Azure Virtual Network (VNet)** is a logically isolated network in Azure that allows resources (VMs, databases, services) to securely communicate with each other, the internet, and on-premises networks.

### Key Features

- **Isolation**: VNets provide isolation at the network level for segmenting resources and controlling traffic
- **Subnetting**: Divide a VNet into subnets for resource organization and traffic control
- **Address Space**: VNets have an address space defined using CIDR notation, determining the IP address range

---

## Subnets & CIDR

### Subnets

Subnets are subdivisions of a Virtual Network, allowing for better organization and traffic management.

**Example:**
- `10.0.1.0/24` → Web Subnet
- `10.0.2.0/24` → Database Subnet

### CIDR (Classless Inter-Domain Routing)

CIDR notation represents IP addresses and their routing prefix, specifying the range of IP addresses for a network.

**Example:**
- `10.0.0.0/16` → IP range for entire VNet

---

## IP Addressing

### Private IP Addresses
- Used for internal communication within VNet
- Not accessible from the internet
- Example: `10.0.1.5`

### Public IP Addresses
- Used for internet access
- Assigned to resources that need external connectivity
- Example: Resources facing the internet

---

## Routes & Route Tables

### Routes

Routes dictate how network traffic is directed, specifying the destination and next hop.

### Route Tables

Route Tables are collections of routes associated with subnets, enabling custom routing rules. They control traffic flow within and outside the VNet.

---

## Network Security Groups (NSGs)

NSGs act like firewalls and are fundamental for Azure's network security, allowing filtering of inbound and outbound traffic.

### Key Aspects

| Aspect | Details |
|--------|---------|
| **Rules** | Define allowed or denied traffic based on source, destination, port, and protocol |
| **Default Rules** | NSGs have default rules for controlling traffic within the Virtual Network |
| **Association** | Can be associated with subnets or individual network interfaces |
| **Principle** | Use least privilege (allow only necessary traffic) |

---

## Application Security Groups (ASGs)

### Purpose

ASGs group Azure virtual machines based on application requirements, simplifying network security management.

### Benefits

- **Simplification**: Define rules based on application roles instead of individual IP addresses
- **Dynamic Membership**: Support dynamic membership based on tags or other attributes
- **Scalability**: Intuitive and scalable network security management
- **Rule Association**: Security rules can be associated with ASGs

---

## Communication Types

### 1. VM to VM (Same VNet)
- Uses private IP addresses
- Fast & secure communication

### 2. Internet Communication
- Via Public IP + NSG rules
- Requires appropriate security configuration

### 3. VNet Peering
- Connects two VNets
- Low latency, high-speed communication

### 4. On-Premises Connection
- **VPN Gateway**: Encrypted connection
- **ExpressRoute**: Private, dedicated connection

---

## VNet Architecture

### Flat Architecture
- All resources in one VNet
- Suitable for small deployments

### Hub-Spoke Architecture (Recommended)
- **Hub**: Contains shared services (firewall, VPN, DNS)
- **Spoke**: Application VNets connected to hub
- Better scalability and security management

---

## Best Practices

1. ✅ Use NSG rules with least privilege principle
2. ✅ Avoid opening all ports (0-65535)
3. ✅ Use private IP addresses whenever possible
4. ✅ Use Azure Bastion instead of public SSH access
5. ✅ Enable logging & monitoring on NSGs
6. ✅ Implement Hub-Spoke architecture for complex environments
7. ✅ Use NSG Flow Logs for traffic analysis

---

## Common VNet Services

| Service | Purpose |
|---------|---------|
| Azure Virtual Network | Network container |
| Azure Load Balancer | Distribute traffic |
| Azure Application Gateway | Advanced load balancing with web app firewall |
| Azure Bastion | Secure RDP/SSH access without public IPs |
| Azure VPN Gateway | Site-to-site/point-to-site connectivity |

---

## Quick Creation Steps

1. Go to **Azure Portal**
2. Search **Virtual Network**
3. Click **Create**
4. Enter Configuration:
   - Name
   - Region
   - Address space (e.g., `10.0.0.0/16`)
5. Add Subnets
6. Configure NSGs
7. Review + Create

---

## Quick Summary Table

| Component | Purpose | Example |
|-----------|---------|---------|
| VNet | Network container | `10.0.0.0/16` |
| Subnet | Divide network | `10.0.1.0/24` |
| NSG | Security/firewall | Allow port 443 |
| Public IP | Internet access | VMs facing internet |
| Private IP | Internal communication | VM to VM |
| Peering | Connect VNets | VNet A ↔ VNet B |
| Route Table | Traffic control | Custom routes |

---

## 🎯 Interview One-Liner

👉 **Azure VNet is a logically isolated network that enables secure communication between Azure resources, the internet, and on-premises environments with granular security control via NSGs.**

---

## 🧠 Quick Revision Flow

```
VNet → Subnet → IP Addressing → NSG Rules → Routing → Connectivity (Peering/VPN/ExpressRoute)
```

---
