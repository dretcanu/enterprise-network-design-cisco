# Testing Documentation

## Overview

This document summarises the testing and validation performed for the EmboArts enterprise network.

Testing was used to confirm connectivity, routing, DHCP, NAT, wireless access, gateway reachability and performance.

---

## Testing Methodology

Testing followed a structured approach:

1. Verify device connectivity
2. Confirm VLAN operation
3. Test inter-VLAN routing
4. Validate DHCP services
5. Test internet access through NAT/PAT
6. Verify Static NAT to DMZ servers
7. Test wireless connectivity
8. Record performance metrics
9. Document limitations and issues

---

## Test Categories

| Category | Purpose |
|---|---|
| Intra-VLAN Connectivity | Confirm devices in same VLAN can communicate |
| Inter-VLAN Routing | Confirm routing between VLANs |
| Internet Connectivity | Confirm external reachability |
| NAT/PAT | Confirm address translation |
| Static NAT | Confirm DMZ server publishing |
| DHCP | Confirm dynamic addressing |
| Wireless | Confirm guest wireless operation |
| Gateway Operations | Confirm default gateway reachability |
| Performance | Confirm latency and packet loss |

---

## Results Summary

| Test Area | Result |
|---|---|
| Intra-VLAN Connectivity | Passed |
| Inter-VLAN Routing | Passed |
| DHCP Services | Passed |
| NAT/PAT | Passed |
| Static NAT | Passed |
| Wireless Connectivity | Passed |
| Gateway Reachability | Passed |
| Performance Baseline | Passed |
| ACL Enforcement | Limited by Packet Tracer behaviour |

Overall result:

- 43 functional tests performed
- 84% overall success rate
- 100% success in critical areas
- 0% packet loss in successful connectivity tests

---

## Performance Results

| Metric | Result |
|---|---:|
| Internal wired latency | <1 ms |
| Wireless average latency | 17 ms |
| Wireless packet loss | 0% |
| NAT translated packets | 757 |
| Active NAT translations | 181 |

---

## NAT Validation

NAT/PAT testing confirmed that multiple internal devices could share the public IP address using port translation.

Static NAT was also validated for DMZ servers:

| DMZ Service | Internal IP | Public IP |
|---|---:|---:|
| Web Server | 192.168.99.10 | 203.0.113.10 |
| Email Server | 192.168.99.20 | 203.0.113.11 |

---

## Wireless Testing

Wireless testing confirmed:

- Guest wireless clients could connect to the network
- Wireless clients could reach their default gateway
- Wireless clients could access external resources
- Average wireless latency was approximately 17 ms
- Packet loss was 0%

---

## Example Test Evidence to Add as Screenshots

Add screenshots of the following Packet Tracer outputs:

- `show vlan brief`
- `show interfaces trunk`
- `show ip route`
- `show ip dhcp pool`
- `show ip nat translations`
- Successful ping tests
- Traceroute output
- Wireless client connection
- Port Security verification
- DHCP Snooping verification

Place these screenshots in the `screenshots/` folder.

---

## Testing Conclusion

Testing confirmed that the network met its main technical objectives. Critical services including VLAN connectivity, inter-VLAN routing, DHCP, NAT/PAT, wireless connectivity and gateway reachability were successfully validated.
