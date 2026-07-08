# Enterprise Campus Network Design & Implementation

<div align="center">

# Enterprise Campus Network

**Cisco Packet Tracer • Enterprise Networking • Infrastructure • Network Security**

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet%20Tracer-1BA0D7?style=for-the-badge)
![Enterprise](https://img.shields.io/badge/Enterprise-Network-success?style=for-the-badge)
![Layer 3](https://img.shields.io/badge/Layer_3-Routing-blue?style=for-the-badge)
![Security](https://img.shields.io/badge/Secure-Design-red?style=for-the-badge)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Business Scenario](#business-scenario)
- [Enterprise Topology](#enterprise-topology)
- [Architecture](#architecture)
- [Key Features](#key-features)
- [VLAN Design](#vlan-design)
- [Security Features](#security-features)
- [Implementation Evidence](#implementation-evidence)
- [Technologies Used](#technologies-used)
- [Skills Demonstrated](#skills-demonstrated)
- [Repository Structure](#repository-structure)
- [Future Enhancements](#future-enhancements)

---

# Overview

This project demonstrates the design, implementation and validation of a secure **Enterprise Campus Network** for **EmboArts Solutions** using **Cisco Packet Tracer**.

The implementation follows enterprise networking principles including:

- Hierarchical campus architecture
- Layer 3 switching
- VLAN segmentation
- Inter-VLAN routing
- DHCP
- NAT/PAT
- Static NAT
- SSH administration
- Port Security
- DHCP Snooping
- DMZ
- Guest Wireless

---

# Business Scenario

EmboArts Solutions required a secure, scalable and manageable network capable of supporting multiple departments, public-facing services and guest wireless access while maintaining strong separation between business systems.

---

# Enterprise Topology

> Replace the image below with your final topology screenshot.

![Enterprise Topology](screenshots/01-topology-overview.png)

---

# Architecture

```
                Internet
                    │
              ISP Router
                    │
             Enterprise Router
                    │
          Cisco Catalyst 3650
               Layer 3 Core
          ┌─────────┼─────────┐
          │         │         │
     Access SW   Access SW   DMZ SW
          │         │         │
 Management   Finance/Sales   Web Server
 IT Dept                      Email Server

             Guest Wireless
```

---

# Key Features

| Feature | Status |
|---------|:-----:|
| Hierarchical Design | ✅ |
| Layer 3 Routing | ✅ |
| VLAN Segmentation | ✅ |
| DHCP | ✅ |
| NAT/PAT | ✅ |
| Static NAT | ✅ |
| SSH | ✅ |
| DHCP Snooping | ✅ |
| Port Security | ✅ |
| Guest Wireless | ✅ |
| DMZ | ✅ |

---

# VLAN Design

| VLAN | Department | Subnet |
|---:|---|---|
|10|Management|192.168.10.0/24|
|20|IT Operations|192.168.20.0/24|
|30|Finance|192.168.30.0/24|
|40|Sales|192.168.40.0/24|
|99|DMZ|192.168.99.0/24|
|100|Guest Wireless|192.168.100.0/24|

---

# Security Features

- SSH secure remote administration
- VLAN segmentation
- Port Security
- DHCP Snooping
- DMZ isolation
- Static NAT for public servers
- Guest Wireless separation

---

# Implementation Evidence

## Enterprise Topology

![Topology](screenshots/01-topology-overview.png)

## VLAN Configuration

![VLAN](screenshots/02-vlan-configuration.png)

## Trunk Links

![Trunks](screenshots/03-trunk-links.png)

## Routing Table

![Routing](screenshots/04-routing-table.png)

## DHCP

![DHCP](screenshots/05-dhcp-services.png)

## NAT

![NAT](screenshots/06-nat-translations.png)

## Guest Wireless Validation

![Connectivity](screenshots/07-connectivity-test.png)

The validation confirms:

- Successful VLAN implementation
- Operational inter-VLAN routing
- DHCP address allocation
- NAT translation
- Internet connectivity
- Guest network isolation

---

# Technologies Used

- Cisco Packet Tracer
- Cisco IOS
- Cisco Catalyst 3650
- Cisco Catalyst 2960
- Cisco 2911 Router
- IPv4
- VLANs
- Layer 3 Switching
- DHCP
- NAT/PAT
- Static NAT
- SSH
- Port Security
- DHCP Snooping

---

# Skills Demonstrated

- Enterprise Network Design
- Switching & Routing
- Infrastructure Design
- Network Security
- Technical Documentation
- Network Validation
- Troubleshooting

---

# Repository Structure

```text
enterprise-campus-network-design/
├── README.md
├── lab/
├── screenshots/
├── diagrams/
├── docs/
└── report/
```

---

# Future Enhancements

- OSPF
- HSRP
- IPv6
- EtherChannel
- Cisco ASA Firewall
- SNMP
- Syslog
- Python Automation
- Ansible

---

# Author

**Vasile C. Dretcanu**

Aspiring Network & Infrastructure Engineer

GitHub: https://github.com/dretcanu
