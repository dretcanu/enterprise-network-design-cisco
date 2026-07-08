# Lessons Learned

## Overview

This project strengthened practical understanding of enterprise network design, Cisco IOS configuration, security controls, troubleshooting and technical documentation.

It also highlighted important differences between a simulated environment and a production Cisco deployment.

---

## Key Lessons

## 1. Documentation Should Be Created During Implementation

One of the most important lessons was the value of documenting decisions, commands and test results during implementation rather than after the network is complete.

Good documentation makes troubleshooting easier and improves the quality of final technical reporting.

---

## 2. VLAN Design Improves Security and Manageability

Separating departments into VLANs made the network easier to understand, secure and troubleshoot.

VLAN segmentation helped isolate Management, IT Operations, Finance, Sales, DMZ and Guest Wireless traffic.

---

## 3. Layer 3 Switching Is More Suitable Than Router-on-a-Stick for This Design

Using a Layer 3 core switch allowed inter-VLAN routing to be handled centrally and efficiently through SVIs.

This reflects a more scalable enterprise approach than relying on router-on-a-stick for all VLAN routing.

---

## 4. Packet Tracer Has Simulation Limitations

Some security features did not behave exactly as expected in Packet Tracer.

Examples included:

- ACL application to Switch Virtual Interfaces
- Port Security sticky MAC learning behaviour

These limitations were documented and treated as simulation constraints rather than design failures.

---

## 5. Testing Is as Important as Configuration

The project showed that configuration alone is not enough. Each feature needs validation.

Testing confirmed:

- Connectivity
- Routing
- DHCP
- NAT/PAT
- Wireless access
- Gateway reachability
- Performance

---

## 6. Security Requires Multiple Layers

No single security feature protects the whole network. A layered approach is stronger.

This project combined:

- VLAN segmentation
- SSH
- NAT
- Port Security
- DHCP Snooping
- Guest isolation
- DMZ separation
- ACL design

---

## What I Would Improve in a Production Version

Future improvements would include:

- OSPF or EIGRP dynamic routing
- HSRP or VRRP gateway redundancy
- EtherChannel uplinks
- IPv6 dual-stack support
- Cisco ASA or Firepower firewall
- RADIUS or TACACS+ authentication
- 802.1X port authentication
- Centralised Syslog
- SNMP or NetFlow monitoring
- Wireless LAN Controller
- Network automation with Python or Ansible

---

## Final Reflection

This project helped connect networking theory with practical implementation. It also demonstrated the importance of structured design, security planning, testing evidence and clear technical documentation.

The final result is a strong foundation for further study in network engineering, infrastructure engineering and cybersecurity.
