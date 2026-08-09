Intro to LAN

**Category:** Networking Fundamentals  
**Difficulty:** Easy  


## Overview
This repository contains my documentation and summary notes for the **Intro to LAN** room on TryHackMe. The room covers the fundamental architecture of Local Area Networks, device roles, hardware behavior, and how data moves within localized environments.


## Key Concepts & Learnings

### 1. LAN Architecture & Topologies
- **Local Area Network (LAN):** A network connecting computer devices within a limited physical region (e.g., homes, offices, labs).
- **Network Topologies:**
  - **Star Topology:** Devices connect directly to a central node (switch/hub). Highly scalable and the modern default.
  - **Bus Topology:** Devices share a single backbone cable; susceptible to single points of failure.
  - **Ring Topology:** Data travels in one direction around a circle; failure of one node can disrupt the loop.

### 2. Core Network Hardware
- **Hubs (Layer 1):** Repeat incoming traffic to every port, creating a single large collision domain and increasing packet-sniffing risks.
- **Switches (Layer 2):** Intelligently forward frames to specific ports using MAC Address Tables, reducing collision domains and improving privacy.
- **Routers (Layer 3):** Connect distinct networks (LAN to WAN/Internet) and route packets based on IP addresses.

### 3. Physical & Logical Addressing
- **MAC Address:** A unique 48-bit physical address embedded in the Network Interface Card (NIC) by the manufacturer.
- **IP Address:** A logical 32-bit (IPv4) or 128-bit (IPv6) address assigned to represent a host on a given network segment.
- **Frame Encapsulation:** Understanding how payload data is wrapped in headers (IP headers, Ethernet frames) for local delivery.


## Practical Takeaways for Security
- Unmanaged switches and hubs expose network segments to promiscuous mode sniffing and broadcast spam.
- Segmenting networks and understanding local broadcast domains form the foundation for identifying ARP spoofing, VLAN hopping, and lateral movement paths.


