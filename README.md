# Cisco Routing Infrastructure, NAT Overload & Packet Capture Auditing

## Overview
This repository brings together enterprise routing implementations on Cisco 1900/2900 Series Integrated Services Routers (ISRs), physical and virtual server infrastructure audits, and deep packet inspection (DPI) using Wireshark. It documents the mechanics of network address translation, frame encapsulation overhead, IP datagram fragmentation, and Address Resolution Protocol (ARP) resolution workflows.

---

## Technical Implementations

### 1. Cisco IOS Routing & Dynamic NAT Overload (PAT)
* **Subnet & Gateway Provisioning:** Configured Cisco ISRs via CLI across GigabitEthernet interfaces (`Gi0/0` LAN and `Gi0/1` WAN) with static routing to upstream gateway interfaces (`172.20.0.1`).
* **NAT Overload Configuration:** Implemented Port Address Translation (PAT) translating internal private subnets (`192.168.0.0/24`) to external interface addresses:
  ```text
  interface GigabitEthernet0/0
   ip nat inside
  interface GigabitEthernet0/1
   ip nat outside
  ip nat inside source list 1 interface GigabitEthernet0/1 overload
  access-list 1 permit 192.168.0.0 0.0.0.255
