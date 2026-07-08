# Security Documentation

## Overview

This document explains the security controls implemented in the EmboArts enterprise network.

The design applies a defence-in-depth approach using VLAN segmentation, secure management, port security, DHCP Snooping, NAT and guest wireless isolation.

---

## Security Objectives

The main security objectives were:

- Separate departments using VLANs
- Protect sensitive Finance and Management systems
- Isolate public-facing services in a DMZ
- Prevent guest wireless users from accessing internal resources
- Secure remote device administration
- Reduce risk from unauthorised devices
- Protect DHCP infrastructure from rogue DHCP servers

---

## VLAN Segmentation

VLANs separate traffic into different broadcast domains.

| VLAN | Security Purpose |
|---:|---|
| 10 | Management network |
| 20 | IT Operations network |
| 30 | Finance network with enhanced isolation |
| 40 | Sales network |
| 99 | DMZ for public-facing services |
| 100 | Guest Wireless network |

Segmentation reduces unnecessary exposure between departments and supports controlled communication through Layer 3 routing.

---

## Secure Management

Remote management was configured using SSH instead of Telnet.

Security measures include:

- SSH Version 2
- Telnet disabled
- Enable secret password
- Service password encryption
- Login banners
- VTY access restrictions

SSH provides encrypted remote access and avoids sending credentials in clear text.

---

## DMZ Security

The DMZ hosts public-facing services:

| Server | Internal IP | Public NAT IP |
|---|---:|---:|
| Web Server | 192.168.99.10 | 203.0.113.10 |
| Email Server | 192.168.99.20 | 203.0.113.11 |

The DMZ separates externally reachable services from internal business networks.

---

## NAT Security

NAT provides security by hiding private internal addressing from external networks.

PAT allows internal clients to access external services using a shared public IP address, while Static NAT provides controlled public access to specific DMZ servers.

---

## Port Security

Port Security was configured on access switch ports to reduce the risk of unauthorised devices being connected to the network.

Standard configuration concept:

```text
switchport mode access
switchport port-security
switchport port-security maximum 2
switchport port-security violation shutdown
switchport port-security mac-address sticky
```

This limits the number of MAC addresses allowed on each access port.

---

## DHCP Snooping

DHCP Snooping was implemented to protect against rogue DHCP servers.

Trusted ports:

- Uplinks to the CoreSwitch

Untrusted ports:

- End-user access ports

This prevents unauthorised devices from acting as DHCP servers and issuing incorrect gateway or DNS information.

---

## ACL Design

ACLs were designed for:

- Guest network restrictions
- Finance network restrictions
- DMZ isolation

Packet Tracer limitations prevented full functional application of ACLs to SVIs in the simulated environment, but the ACL design demonstrates correct security planning and policy intent.

---

## Wireless Security

The guest wireless network uses:

- WPA2-PSK
- AES encryption
- Guest VLAN isolation
- Dedicated VLAN 100

The purpose is to allow visitors internet access without exposing internal resources.

---

## Packet Tracer Limitations

Two key limitations were documented:

1. ACLs applied to SVIs did not behave as expected in Packet Tracer.
2. Port Security sticky MAC learning showed secure-down behaviour in some tests.

In a production Cisco environment, these features would be expected to operate differently depending on platform, IOS version and configuration support.

---

## Security Summary

| Control | Purpose |
|---|---|
| VLANs | Logical segmentation |
| SSH | Secure administration |
| NAT/PAT | Address hiding and internet access |
| Static NAT | Controlled DMZ publishing |
| Port Security | Physical access control |
| DHCP Snooping | Rogue DHCP protection |
| WPA2 | Wireless authentication |
| ACLs | Traffic filtering policy design |
