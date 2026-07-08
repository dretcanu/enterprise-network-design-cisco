# Network Design Documentation

## Overview

This document explains the design of the EmboArts enterprise network. The network was built to support multiple departments, public-facing services, internet access, wireless guest access and secure network administration.

The design uses a hierarchical model with a Layer 3 core switch, access switches, an edge router, a simulated ISP router, a DMZ and a guest wireless network.

---

## Business Scenario

EmboArts is a fictional medium-sized creative agency requiring secure and segmented network services for:

- Management
- IT Operations
- Finance
- Sales
- Public-facing DMZ services
- Guest wireless users

The design focuses on scalability, security, maintainability and reliable access to internal and external services.

---

## Architecture Summary

The physical topology includes:

| Component | Device / Role |
|---|---|
| Core Layer | Cisco Catalyst 3650-24PS Layer 3 Switch |
| Access Layer | Three Cisco Catalyst 2960-24TT Switches |
| Edge | Cisco 2911 Router |
| ISP | Cisco 2911 Router |
| Wireless | Cisco AccessPoint-PT |
| End Devices | PCs, servers, printers and laptops |

The distribution layer is functionally collapsed into the core switch, which is appropriate for a medium-sized network and simplifies management.

---

## VLAN Design

| VLAN | Function | Network | Gateway |
|---:|---|---|---|
| 10 | Management | 192.168.10.0/24 | 192.168.10.1 |
| 20 | IT Operations | 192.168.20.0/24 | 192.168.20.1 |
| 30 | Finance | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Sales | 192.168.40.0/24 | 192.168.40.1 |
| 99 | DMZ | 192.168.99.0/24 | 192.168.99.1 |
| 100 | Guest Wireless | 192.168.100.0/24 | 192.168.100.1 |

VLAN segmentation was used to separate business functions, reduce broadcast traffic and improve security.

---

## Device Placement

| Switch | Purpose |
|---|---|
| Switch0 | Management, IT Operations and Finance |
| Switch1 | Sales |
| Switch2 | DMZ servers and wireless access point |

The CoreSwitch aggregates all access switches using trunk links and provides Layer 3 routing through Switch Virtual Interfaces.

---

## Trunk Links

| Link | Purpose |
|---|---|
| CoreSwitch Gi1/0/2 ↔ Switch0 Fa0/24 | VLAN trunk |
| CoreSwitch Gi1/0/3 ↔ Switch1 Fa0/24 | VLAN trunk |
| CoreSwitch Gi1/0/4 ↔ Switch2 Fa0/24 | VLAN trunk |

Each trunk carries VLANs 10, 20, 30, 40, 99 and 100.

---

## IP Addressing Plan

Each VLAN uses a /24 subnet. The first part of each subnet is reserved for gateways, servers, printers and infrastructure devices, while DHCP pools provide dynamic addressing for clients.

| VLAN | DHCP Range |
|---:|---|
| 10 | 192.168.10.150 - 192.168.10.200 |
| 20 | 192.168.20.150 - 192.168.20.200 |
| 30 | 192.168.30.150 - 192.168.30.200 |
| 40 | 192.168.40.150 - 192.168.40.200 |
| 100 | 192.168.100.10 - 192.168.100.200 |

DMZ servers use static addressing.

---

## Important Static Assignments

| Device | IP Address | VLAN |
|---|---:|---:|
| PC-Mgmt | 192.168.10.10 | 10 |
| PC-IT | 192.168.20.10 | 20 |
| Server-IT | 192.168.20.20 | 20 |
| PC-Finance | 192.168.30.10 | 30 |
| PC-Sales | 192.168.40.10 | 40 |
| Server-Web | 192.168.99.10 | 99 |
| Server-Email | 192.168.99.20 | 99 |
| WAP0 | 192.168.100.254 | 100 |
| Laptop0 | 192.168.100.50 | 100 |
| Laptop1 | 192.168.100.51 | 100 |

---

## Routing Design

Inter-VLAN routing is performed by the Layer 3 CoreSwitch using SVIs.

The CoreSwitch forwards non-local traffic to the edge router using a default route:

```text
ip route 0.0.0.0 0.0.0.0 192.168.1.1
```

The edge router then forwards traffic toward the ISP router.

Static routing was selected because the topology is small, predictable and does not require dynamic routing complexity.

---

## NAT Design

The network uses two NAT approaches:

| NAT Type | Purpose |
|---|---|
| PAT | Allows internal clients to share one public IP address |
| Static NAT | Provides public access to DMZ web and email servers |

Static NAT mappings:

| Internal Server | Public IP |
|---|---|
| 192.168.99.10 | 203.0.113.10 |
| 192.168.99.20 | 203.0.113.11 |

---

## Wireless Design

The guest wireless network uses:

- SSID: EmboArts-Guest
- Security: WPA2-PSK
- Encryption: AES
- VLAN: 100
- Gateway: 192.168.100.1

Guest wireless traffic is separated from internal business VLANs.

---

## Design Rationale

The design balances:

- Security through segmentation
- Simplicity through static routing
- Scalability through VLAN-based addressing
- Performance through Layer 3 switching
- Manageability through structured documentation
