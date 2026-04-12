# Day 6: Azure Networking Advanced

---

## Table of Contents

1. [Azure Networking Overview](#azure-networking-overview)
2. [Core Components](#core-components)
3. [Connectivity Services](#connectivity-services)
4. [Load Balancing & Traffic Management](#load-balancing--traffic-management)
5. [Security Services](#security-services)
6. [Routing & Traffic Control](#routing--traffic-control)
7. [Architecture Patterns](#architecture-patterns)
8. [Advanced Concepts](#advanced-concepts)
9. [Best Practices](#best-practices)

---

## Azure Networking Overview

### Definition

**Azure Networking** is a collection of services that enables secure communication between Azure resources, the internet, and on-premises environments.

### Network Layering Model

```
User/Internet
   ↓
Layer 7 (Application) → Application Gateway, Traffic Manager
   ↓
Layer 4 (Transport) → Load Balancer
   ↓
Security Layer → NSG, Azure Firewall, WAF
   ↓
VNet/Subnet
   ↓
Azure Resources (VMs, Databases, Services)
```

---

## Core Components

### 1. Virtual Network (VNet)

- **Definition**: Private network in Azure
- **Similar to**: AWS VPC
- **Contains**: Subnets, resources, security policies
- **Scope**: Regional
- **Address Space**: Defined using CIDR notation (e.g., 10.0.0.0/16)

---

### 2. Subnet

- Smaller network inside VNet
- Used to organize resources by function
- **Common Organization**:
  - `10.0.1.0/24` → Web Tier
  - `10.0.2.0/24` → Application Tier
  - `10.0.3.0/24` → Database Tier

---

### 3. IP Address Types

| Type | Description | Use Case |
|------|-------------|----------|
| **Public IP** | Internet-routable address | External communication, VMs facing internet |
| **Private IP** | Internal network address | VM-to-VM communication, databases |
| **Dynamic IP** | Assigned/changed as needed | Temporary deployments |
| **Static IP** | Permanent assignment | Production servers, DNS records |

---

### 4. Network Security Group (NSG)

- Acts as a **firewall** for controlling traffic
- Defines **inbound and outbound rules**
- Can be applied at **subnet or NIC level**
- **Default Rules**: Allow VNet communication, allow Azure load balancer, deny all else

---

### 5. Azure DNS

**Definition**: Scalable and secure domain hosting service that provides name resolution using the Microsoft Azure infrastructure.

**Key Features**:
- **Domain Hosting**: Hosts domain names and provides name resolution within Azure
- **Integration with Azure Services**: Easily integrates with other Azure services like App Service and Traffic Manager
- **Global Availability**: Provides low-latency responses globally
- **Private DNS Zones**: Support for private domain resolution
- **DNS Records Management**: Full control over DNS records (A, AAAA, CNAME, MX, TXT, etc.)

---

## Connectivity Services

### 1. Internet Connectivity

**Components**: Public IP + NSG rules

- Resources get assigned Public IP
- NSG allows inbound/outbound rules
- Resources can communicate with internet

---

### 2. VNet Peering

**Purpose**: Connect VNets directly

**Definition**: Allows connecting Azure Virtual Networks directly, enabling resources in one VNet to communicate with resources in another.

| Feature | Details |
|---------|---------|
| **Scope** | Can be same region or cross-region (global peering) |
| **Performance** | High speed, low latency |
| **Transitivity** | Direct traffic path between peered VNets |
| **Security** | Private connection, no internet traversal |
| **Global VNet Peering** | Peering can be established across regions |
| **Bandwidth** | No bandwidth limitations |

**Key Benefits**:
- Low latency, high-speed communication
- Direct traffic path between peered VNets
- Private, secure connectivity
- Cross-region support for global deployments

---

### 3. VPN Gateway

**Purpose**: Secure connection between Azure and On-Premises

**Definition**: Provides secure, site-to-site connectivity between your on-premises network and Azure with multiple VPN connection types.

| Type | Details |
|------|---------|
| **Site-to-Site VPN** | Connects on-premises networks to Azure over an encrypted VPN tunnel |
| **Point-to-Site VPN** | Enables secure remote access to Azure resources from individual devices |
| **VNet-to-VNet** | Connects two Azure VNets using VPN Gateway |

**Key Features**:
- **IPsec/IKE VPN Protocols**: Ensures secure communication over the Internet
- **High Availability**: Supports active-active and active-passive configurations for high availability
- **BGP Support**: Allows dynamic routing between your on-premises network and Azure
- **SSL/TLS Support**: Secure encrypted connections for remote users

---

### 4. VNet Gateway (Virtual Network Gateway)

**Purpose**: Enable secure communication between on-premises networks and Azure Virtual Networks

**Definition**: Provides connectivity between Azure Virtual Networks and on-premises networks with encrypted tunnels supporting multiple connection types.

| Connection Type | Purpose |
|-----------------|---------|
| **Site-to-Site VPN** | Connects on-premises networks to Azure over an encrypted VPN tunnel for branch office connectivity |
| **Point-to-Site VPN** | Enables secure remote access to Azure resources for individual users and remote devices |
| **VNet-to-VNet** | Connects two Azure Virtual Networks for cross-region or cross-subscription communication |

**Key Capabilities**:
- Secure encrypted connections (IPsec/IKE protocols)
- Dynamic and static routing options
- BGP support for dynamic routing announcements
- Active-active and active-passive high availability configurations

---

### 5. ExpressRoute

**Purpose**: Private, high-performance connectivity

- **No internet traversal** - fully private connection
- **Dedicated connection** from on-premises to Azure
- **High security & performance**
- **Consistent latency**
- Option for private peering, public peering, Microsoft peering

---

## Load Balancing & Traffic Management

### 1. Azure Load Balancer (Layer 4)

**Layer**: Layer 4 (TCP/UDP)

**Definition**: Distributes incoming network traffic across multiple servers to ensure no single server is overwhelmed.

| Feature | Details |
|---------|---------|
| **Purpose** | Distributes traffic across multiple servers |
| **Scope** | Internal or external (public) |
| **Load Balancing Algorithms** | Supports round-robin, least connections, and other distribution methods |
| **HA Support** | Works seamlessly with availability sets to ensure high availability |
| **Traffic Direction** | Balances both inbound and outbound traffic |
| **Health Probes** | Monitors health of backend instances |

**Key Capabilities**:
- Distributes incoming traffic across multiple servers
- Ensures no single server is overwhelmed
- Supports different algorithms for traffic distribution
- Works seamlessly with availability sets for high availability

---

### 2. Azure Application Gateway

**Layer**: Layer 7 (HTTP/HTTPS)

**Definition**: Web traffic load balancer that enables you to manage and route traffic to your web applications with advanced features like WAF and SSL termination.

| Feature | Details |
|---------|---------|
| **URL Routing** | Route based on URL path or hostname |
| **SSL Termination** | Offloads SSL/TLS processing, improving the efficiency of backend servers |
| **WAF** | Web Application Firewall protects against common web vulnerabilities and exploits |
| **Cookies** | Session affinity support |
| **Multi-site Hosting** | Host multiple websites |
| **Request Rewriting** | Rewrite HTTP headers and URL paths |

**Key Features**:
- **Load Balancing**: Distributes incoming traffic across multiple servers to ensure no single server is overwhelmed
- **SSL Termination**: Offloads SSL processing, improving the efficiency of web servers
- **Web Application Firewall (WAF)**: Protects web applications from common web vulnerabilities and exploits
- **Advanced Routing**: URL-based and hostname-based routing for complex scenarios

---

### 3. Azure Traffic Manager

**Type**: DNS-based routing

| Feature | Details |
|---------|---------|
| **Purpose** | Global traffic distribution |
| **Scope** | Routes across regions |
| **Methods** | Priority, weighted, performance, geographic, multi-value |
| **Health Checks** | Automatic failover based on endpoint health |

---

## Security Services

### 1. Azure Firewall

**Type**: Managed, cloud-based network security service

**Definition**: Protects your Azure Virtual Network resources with intelligent threat protection and network access controls.

| Feature | Details |
|---------|---------|
| **Stateful Firewall** | Allows/denies traffic based on rules with state tracking and stateful inspection |
| **FQDN Filtering** | Filter traffic based on fully qualified domain names (application layer) |
| **Threat Intelligence** | Integrates with threat intelligence feeds for enhanced security |
| **Centralized Management** | Single point of security management for multiple VNets |
| **Logging & Monitoring** | Detailed logging for compliance & analysis |

**Key Capabilities**:
- **Stateful Firewall**: Allows or denies traffic based on rules and supports stateful inspection
- **Application FQDN Filtering**: Filters traffic based on fully qualified domain names
- **Threat Intelligence Integration**: Integrates with threat intelligence feeds for enhanced security
- **Centralized Security**: Single point for managing security policies across multiple VNets

---

### 2. Web Application Firewall (WAF)

- Protects web applications from common vulnerabilities:
  - SQL Injection
  - Cross-Site Scripting (XSS)
  - DDoS attacks
  - Malicious bots
- Integrates with Application Gateway or Front Door

---

### 3. Azure DDoS Protection

**Purpose**: Protects against Distributed Denial of Service attacks

- **Standard Tier**: Basic protection for all Azure customers
- **Premium Tier**: Advanced protection, 24/7 monitoring, attack mitigation

---

### 4. Azure Bastion

**Purpose**: Secure SSH/RDP access without public IPs

| Benefit | Details |
|---------|---------|
| **No Public IP** | VMs don't need public IPs |
| **Security** | All traffic encrypted |
| **Convenience** | Direct access from Azure Portal |
| **Control** | Fine-grained access control |

---

## Routing & Traffic Control

### 1. Route Tables (User-Defined Routes - UDR)

- Define custom routes for traffic within VNet
- Control traffic flow to specific destinations
- **Use Cases**:
  - Force traffic through firewall
  - Route to on-premises via VPN
  - Direct traffic to Network Virtual Appliance (NVA)

---

### 2. Service Endpoints

- **Purpose**: Secure connection to Azure PaaS services
- **Examples**: Storage, SQL Database, Cosmos DB, Key Vault
- **Security**: Traffic stays within Azure backbone
- **Routing**: Optimized paths to services

---

### 3. Private Endpoints

- **Purpose**: Private access to services (no public internet)
- **Features**:
  - Provisions private IP for service
  - No exposure to public internet
  - Enhanced security
  - Works across subscriptions/tenants

---

## Architecture Patterns

### 1. Hub-Spoke Architecture (Most Important 🔥)

```
                  Hub (Shared Services)
                   ├─ Firewall
                   ├─ VPN Gateway
                   └─ DNS
                      ↑ Peering ↓
        ┌────────────┬─────────────┬─────────────┐
      Spoke1       Spoke2        Spoke3       Spoke4
    (App Tier)   (App Tier)    (App Tier)   (App Tier)
```

**Benefits**:
- Centralized security
- Simplified management
- Cost optimization
- Scalability

---

### 2. Multi-Tier Architecture

```
Internet
   ↓ [Public IP + Load Balancer]
   ↓
Web Tier (10.0.1.0/24)
   ↓ [NSG Rules]
   ↓
App Tier (10.0.2.0/24)
   ↓ [NSG Rules]
   ↓
Database Tier (10.0.3.0/24) [Private]
```

**Characteristics**:
- Each tier in separate subnet
- Controlled traffic flow between tiers
- Enhanced security isolation
- Easy scaling per tier

---

### 3. Hybrid Architecture

- Azure + On-premises via VPN or ExpressRoute
- Shared identity and security policies
- Seamless resource access
- Gradual cloud migration path

---

## Advanced Concepts

### 1. Availability Zones

- Multiple independent data centers
- Within same region but geographically separate
- **Benefits**:
  - High availability
  - Disaster recovery
  - Low latency
  - Fault tolerance

### 2. Load Distribution

- Distribute resources across:
  - Multiple availability zones
  - Multiple regions
  - Multiple VM Scale Sets
- Ensures resilience and performance

---

### 3. Autoscaling

- Automatic VM creation/deletion based on demand
- Integrated with VM Scale Sets
- Metrics: CPU, Memory, Custom metrics
- Reduces costs during low demand

---

### 4. Network Watcher

**Purpose**: Monitor and diagnose network issues

| Feature | Use |
|---------|-----|
| **Topology** | Visualize network architecture |
| **Connection Monitor** | Monitor connectivity between resources |
| **NSG Flow Logs** | Capture traffic flow through NSGs |
| **Packet Capture** | Deep packet inspection |
| **IP Flow Verify** | Test connectivity between VMs |
| **Next Hop** | Troubleshoot routing issues |

---

## Service Comparison Table

| Service | Layer | Use Case | Scope |
|---------|-------|----------|-------|
| **Load Balancer** | Layer 4 | Internal/external traffic distribution | Regional |
| **App Gateway** | Layer 7 | Web app routing, WAF | Regional |
| **Traffic Manager** | DNS | Global routing, failover | Global |
| **Azure Firewall** | Layer 3-7 | Central security, stateful | Regional, multi-VNet |
| **NSG** | Layer 3-4 | VNet/Subnet security | Subnet/NIC level |

---

## Best Practices

### Security

1. ✅ Use **subnets for network segmentation**
2. ✅ Apply **NSG rules with least privilege principle**
3. ✅ Use **private endpoints** instead of public access
4. ✅ **Don't expose VMs directly** to internet
5. ✅ Use **Azure Bastion** for secure SSH/RDP access
6. ✅ Enable **WAF** on Application Gateway
7. ✅ Use **Azure Firewall** for centralized security

### Monitoring & Logging

8. ✅ Enable **NSG Flow Logs** for traffic analysis
9. ✅ Use **Network Watcher** for diagnostics
10. ✅ Configure **Azure Monitor** for alerts
11. ✅ Regular security audits and reviews

### Performance & Reliability

12. ✅ Use **availability zones** for redundancy
13. ✅ Implement **load balancing** for scalability
14. ✅ Enable **autoscaling** for dynamic workloads
15. ✅ Use **caching** to reduce backend load

---

## Real-World End-to-End Flow

```
User/Internet
    ↓
[Public IP + NSG Rules]
    ↓
Azure Application Gateway (Layer 7 - HTTP/HTTPS)
    ├─ URL Routing
    ├─ SSL Termination
    └─ WAF Protection
    ↓
Azure Load Balancer (Layer 4 - TCP/UDP)
    ├─ Distributes across multiple instances
    └─ Health probes
    ↓
VM Web Tier (Public Subnet - 10.0.1.0/24)
    ├─ Application servers
    └─ NSG rules (allow HTTP/HTTPS only)
    ↓
VM App Tier (Private Subnet - 10.0.2.0/24)
    ├─ Business logic
    └─ NSG rules (allow only from Web tier)
    ↓
Database Tier (Private Subnet - 10.0.3.0/24)
    ├─ SQL Database / CosmosDB
    └─ NSG rules (allow only from App tier)
```

---

## 🎯 Interview One-Liner

👉 **Azure Networking provides secure, scalable communication between resources using VNets, subnets, NSGs, load balancers (L4/L7), firewalls, and connectivity services (VPN, ExpressRoute) with centralized management and enterprise-grade security.**

---

## 🧠 Quick Revision Flow

```
VNet → Subnet → NSG → IP Addressing → Routing 
  ↓
Load Balancing (L4 LB, App Gateway) 
  ↓
Security (Firewall, WAF, DDoS Protection) 
  ↓
Connectivity (Peering, VPN, ExpressRoute)
```

---
