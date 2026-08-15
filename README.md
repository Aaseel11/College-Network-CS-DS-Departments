# College-Network-CS-DS-Departments

 College Network Project — Connecting the Data Science and Computer Science Departments

Network topology design connecting the Data Science and Computer Science departments at University of Hail, built in Cisco Packet Tracer. Features two Class C subnets (192.168.10.0/24, 192.168.20.0/24) linked via router serial connection, static routing, DNS resolution per department, and verified inter/intra-network ping connectivity.

Author:Aseel Alanzi — Computer Science Department, University of Hail
Tool Used: Cisco Packet Tracer
Date: November 2025



#  Objective

This project designs and configures two interconnected departmental networks within the College of Computer Science at the University of Hail — one for the Data Science Department and another for the Computer Science Department. It demonstrates core networking concepts including:
- IP addressing
- DNS configuration
- Static routing
- Inter-network communication through routers

# Project Requirements

- Create two separate Class C networks, one per department.
- Connect both networks using two routers linked via a Serial connection.
- Assign IP addresses to all router interfaces (FastEthernet + Serial), servers, and PCs.
- Configure a DNS server in each network to resolve device names to IP addresses.
- Test connectivity using ping between two devices in the same network, by device name.
- Test connectivity using ping between two devices in different networks, by IP address.
- Add clear labels and organize the topology for readability.

# Network Design Overview

The network is composed of two departmental sub-networks connected through a dedicated router-to-router serial link:

| Network | Department | Address |
|---|---|---|
| Network A | Data Science | `192.168.10.0/24` |
| Network B | Computer Science | `192.168.20.0/24` |
| Serial Link | Router-to-Router | `10.10.10.0/30` |

Total devices: 2 routers + 2 switches + 2 DNS servers + 14 PCs (7 per department) = 20 devices

### Data Science Department — IP Addressing

| Device | IP Address | Subnet Mask | Notes |
|---|---|---|---|
| Router0 (Fa0/0) | 192.168.10.1 | 255.255.255.0 | Gateway for Network A |
| PC0 – PC6 | 192.168.10.2 – .8 | 255.255.255.0 | 7 workstations |
| Server0 (DNS) | 192.168.10.10 | 255.255.255.0 | server.datasci.local |
| Router0 (Se0/0/0) | 10.10.10.1 | 255.255.255.252 | Serial link to Router1 |

### Computer Science Department — IP Addressing

| Device | IP Address | Subnet Mask | Notes |
|---|---|---|---|
| Router1 (Fa0/1) | 192.168.20.1 | 255.255.255.0 | Gateway for Network B |
| PC7 – PC13 | 192.168.20.2 – .8 | 255.255.255.0 | 7 workstations |
| Server1 (DNS) | 192.168.20.9 | 255.255.255.0 | server.comp-sci.local |
| Router1 (Se0/0/0) | 10.10.10.2 | 255.255.255.252 | Serial link to Router0 |

# Configuration Summary

# Routing
Static routes were configured on both routers so that each network can reach the other through the serial link:
- **Router0:** route to `192.168.20.0/24` via `10.10.10.2`
- **Router1:** route to `192.168.10.0/24` via `10.10.10.1`

# DNS Configuration
Each department's server runs a DNS service with records mapping every device name in its network to its IP address, including the server's own domain name (`server.datasci.local` and `server.comp-sci.local`). This allows devices to reach one another using names instead of raw IP addresses within the same network.

# Testing & Results

| Test Type | Example | Result |
|---|---|---|
| Ping within the same network (by name) | From PC9, `ping Pc10` resolved via DNS to `192.168.20.3` | Success, 0% loss, TTL=128 |
| Ping between different networks (by IP) | From PC0 (Data Science) to `192.168.20.2` (Computer Science) | Success, TTL=126 (one less, confirming a router hop) |

All required ping tests completed successfully with 0% packet loss, verifying that both routing and DNS configurations work as intended across the full topology.

#  Conclusion

This project successfully demonstrates the design and configuration of two independent departmental networks connected through static routing, with functioning DNS resolution in each network. The topology reflects real-world network segmentation practices — separating departments into distinct subnets while maintaining full inter-department connectivity through a dedicated router link. All connectivity requirements (intra-network ping by name, inter-network ping by IP) were verified and passed successfully.

# Repository Contents


```
College-Network-CS-DS-Departments/
├── README.md
└── docs/
    ├── Network_Project_Report.docx          # Full project report
    ├── Network_Project_Presentation_1.pptx  # Project presentation slides
    └── projct ds,cs networkkwe.pkt                  # Cisco Packet Tracer file
زز
```
# Tools Used

- **Cisco Packet Tracer** — network design and simulation
- **DNS**, **Static Routing**, **IP Addressing (Class C)**

# Author

Aseel Alanzi
Computer Science Department, University of Hail
GitHub: (https://github.com/Aaseel11)
LinkedIn: (https://linkedin.com/in/aseel-alanazi410)
