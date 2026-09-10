# 🧪 Cisco Networking Hands-On Engineering Labs

[![Packet Tracer](https://img.shields.io/badge/Simulator-Cisco%20Packet%20Tracer%208.x-0496ff?style=flat-square&logo=cisco)](https://www.netacad.com/courses/packet-tracer)
[![Cisco IOS](https://img.shields.io/badge/CLI-Cisco%20IOS%20Configuration-1b9aaa?style=flat-square)](https://www.cisco.com)
[![Labs Completed](https://img.shields.io/badge/Labs%20Completed-8%2F30%20Verified-2ec4b6?style=flat-square)](#-lab-execution-matrix)
[![Engineer](https://img.shields.io/badge/Lab%20Engineer-Jaser%20Halabi-10b981?style=flat-square&logo=github)](https://github.com/JaserHalabi)

> A practical, hands-on engineering portfolio featuring custom network topologies, production-grade Cisco IOS CLI configurations, dynamic routing protocols, switching architectures, and empirical connectivity verifications built and tested in **Cisco Packet Tracer**.

---

## 🎯 Hands-On Lab Focus

This repository documents **active network implementations and laboratory experiments**. Rather than passive theory or course notes, every lab represents a real network scenario where topologies are engineered, routers and switches are configured via Cisco IOS CLI, and end-to-end connectivity is rigorously tested and verified.

### 🛠️ Key Engineering Competencies

- **🗺️ Topology Engineering:** Designing multi-router, multi-switch network architectures with custom IPv4/IPv6 subnetting plans (including point-to-point `/30` WAN serial links).
- **💻 Cisco IOS CLI Provisioning:** Writing clean, idempotent configuration scripts for enterprise routers, Catalyst switches, and security appliances.
- **🔀 Routing & Switching:** Deploying static routing, RIP v2, EIGRP, OSPF single/multi-area, VLAN trunking (802.1Q), Inter-VLAN routing, and STP loop avoidance.
- **🛡️ Device Hardening & Security:** Applying MD5 enable secret hashing, service password-encryption, console/VTY authentication, and transport restrictions.
- **🔬 Empirical Connectivity Verification:** Validating data planes through ICMP ping tests, round-trip timing, ARP table inspection, and IOS diagnostic outputs (`show ip route`, `show ip protocols`, `show running-config`).

---

## ⭐ Featured Lab Implementations

Key hands-on labs completed and verified with topologies, configuration scripts, and connectivity captures:

| Lab | Engineering Focus | Key IOS Highlights | Verification Capture |
|---|---|---|---|
| **[Day 09: EIGRP Dynamic Routing](./Day-09-EIGRP/)** | Dynamic routing across dual routers and multiple LAN subnets | `router eigrp <AS>`, `network <net> <wildcard>`, `no auto-summary` | [Topology & Ping Test](./Day-09-EIGRP/ping-verification.png) |
| **[Day 07: RIP Dynamic Routing](./Day-07-RIP/)** | Distance-vector protocol deployment and metric convergence | `router rip`, `version 2`, `network` statements | [Topology & Ping Test](./Day-07-RIP/ping-verification.png) |
| **[Day 06: Static Routing over Serial WAN](./Day-06-Static-Routing/)** | Point-to-point `/30` serial link interconnecting isolated subnets | `interface Serial0/3/0`, `ip route <dest> <mask> <next-hop>` | [Topology & Ping Test](./Day-06-Static-Routing/ping-verification.png) |
| **[Day 05: IPv6 Addressing & Routing](./Day-05-IPv6-Addressing/)** | Dual-stack GUA configuration and neighbor discovery | `ipv6 address <GUA>/64`, `ipv6 enable` | [Topology & Ping Test](./Day-05-IPv6-Addressing/ping-verification.png) |
| **[Day 04: Switch Hardening & Device Security](./Day-04-Basic-Network-Security/)** | Layer 2 switch hardening and access control | `enable secret`, `service password-encryption`, `line vty 0 15` | [Verification Show Run](./Day-04-Basic-Network-Security/verification-show-run.png) |

---

## 📊 Lab Execution Matrix

| # | Lab Workspace | Focus & Implementation Architecture | Status | Completed |
|---|---------------|-------------------------------------|:------:|:---------:|
| 01 | [Day-01-Networking-Devices](./Day-01-Networking-Devices/) | Hardware Identification & Network Device Interfacing | ✅ Complete | 2026-08-19 |
| 02 | [Day-02-Connecting-Devices](./Day-02-Connecting-Devices/) | Physical Media & Cabling Standards (Fiber, Crossover, Straight-Through) | ✅ Complete | 2026-08-19 |
| 03 | [Day-03-OSI-Model](./Day-03-OSI-Model/) | OSI Protocol Analysis & Simulation PDU Inspection | ✅ Complete | 2026-08-19 |
| 04 | [Day-04-Basic-Network-Security](./Day-04-Basic-Network-Security/) | Cisco Switch Hardening, Secret Hashing & Line Security | ✅ Complete | 2026-08-19 |
| 05 | [Day-05-IPv6-Addressing](./Day-05-IPv6-Addressing/) | IPv6 Dual-Stack Addressing & Subnet Provisioning | ✅ Complete | 2026-08-23 |
| 06 | [Day-06-Static-Routing](./Day-06-Static-Routing/) | Dual-Router Static Routing over Point-to-Point /30 Serial WAN | ✅ Complete | 2026-08-24 |
| 07 | [Day-07-RIP](./Day-07-RIP/) | Dynamic Distance-Vector Routing Implementation with RIP v2 | ✅ Complete | 2026-08-24 |
| 08 | [Day-08-OSPF](./Day-08-OSPF/) | OSPF Single-Area Configuration & Neighbor Adjacency | ⬜ Not Started | — |
| 09 | [Day-09-EIGRP](./Day-09-EIGRP/) | Dynamic Enterprise Routing with EIGRP & Metric Verification | ✅ Complete | 2026-08-25 |
| 10 | [Day-10-VLANs](./Day-10-VLANs/) | VLAN Segmentation & 802.1Q Trunking Architecture | ⬜ Not Started | — |
| 11 | [Day-11-Inter-VLAN-Routing](./Day-11-Inter-VLAN-Routing/) | Router-on-a-Stick Inter-VLAN Routing Implementation | ⬜ Not Started | — |
| 12 | [Day-12-STP](./Day-12-STP/) | Spanning Tree Protocol (STP) & Loop Avoidance | ⬜ Not Started | — |
| 13 | [Day-13-EtherChannel](./Day-13-EtherChannel/) | Link Aggregation with EtherChannel (LACP / PAgP) | ⬜ Not Started | — |
| 14 | [Day-14-DHCP](./Day-14-DHCP/) | Enterprise DHCP Server & IP Helper Relay Deployment | ⬜ Not Started | — |
| 15 | [Day-15-DNS](./Day-15-DNS/) | DNS Name Resolution & Server Infrastructure | ⬜ Not Started | — |
| 16 | [Day-16-NAT](./Day-16-NAT/) | Dynamic NAT, Static NAT & Port Address Translation (PAT) | ⬜ Not Started | — |
| 17 | [Day-17-ACLs](./Day-17-ACLs/) | Standard & Extended Access Control Lists (ACLs) | ⬜ Not Started | — |
| 18 | [Day-18-CDP-LLDP](./Day-18-CDP-LLDP/) | Layer 2 Discovery Protocols (CDP & LLDP) | ⬜ Not Started | — |
| 19 | [Day-19-SSH-Telnet](./Day-19-SSH-Telnet/) | Secure Remote Administration (SSH v2 & Telnet Hardening) | ⬜ Not Started | — |
| 20 | [Day-20-NTP](./Day-20-NTP/) | Network Time Protocol (NTP) Synchronization | ⬜ Not Started | — |
| 21 | [Day-21-Syslog-SNMP](./Day-21-Syslog-SNMP/) | Centralized Network Logging & SNMP Monitoring | ⬜ Not Started | — |
| 22 | [Day-22-WAN-PPP](./Day-22-WAN-PPP/) | Point-to-Point WAN Encapsulation (PPP & HDLC) | ⬜ Not Started | — |
| 23 | [Day-23-Frame-Relay](./Day-23-Frame-Relay/) | Legacy WAN & Frame Relay Multipoint Switching | ⬜ Not Started | — |
| 24 | [Day-24-GRE-Tunnels](./Day-24-GRE-Tunnels/) | Site-to-Site Generic Routing Encapsulation (GRE) Tunnels | ⬜ Not Started | — |
| 25 | [Day-25-IPv6-Routing](./Day-25-IPv6-Routing/) | Next-Generation Dynamic IPv6 Routing (OSPFv3) | ⬜ Not Started | — |
| 26 | [Day-26-Wireless-LAN](./Day-26-Wireless-LAN/) | Wireless LAN Infrastructure (WLC & Lightweight APs) | ⬜ Not Started | — |
| 27 | [Day-27-Port-Security](./Day-27-Port-Security/) | Layer 2 Port Security & DHCP Snooping Defense | ⬜ Not Started | — |
| 28 | [Day-28-QoS](./Day-28-QoS/) | Quality of Service (QoS) Queuing & Traffic Prioritization | ⬜ Not Started | — |
| 29 | [Day-29-Network-Automation](./Day-29-Network-Automation/) | Network Automation Basics & Programmability | ⬜ Not Started | — |
| 30 | [Day-30-Capstone-Project](./Day-30-Capstone-Project/) | Enterprise Capstone Architecture Deployment | ⬜ Not Started | — |

### Status Legend

| Badge | Meaning |
|:---:|---|
| ⬜ **Not Started** | Lab scenario scheduled for implementation |
| 🔄 **In Progress** | Currently configuring topology and verifying protocols |
| ✅ **Complete** | Lab fully implemented, verified via CLI / ping, and documented |

---

## 🔬 Lab Methodology & Verification Process

Each lab in this repository follows a four-stage engineering methodology:

```mermaid
graph LR
    A["1. Topology & Subnet Design"] --> B["2. Cisco IOS Configuration"]
    B --> C["3. Protocol Convergence"]
    C --> D["4. Empirical Verification & Capture"]
```

1. **Topology & Subnet Design:** Designing physical and logical network layouts in Cisco Packet Tracer with clear IPv4/IPv6 allocation and link assignments.
2. **Cisco IOS Configuration:** Executing clean, modular CLI configurations across all active routers, Catalyst switches, and network security devices.
3. **Protocol Convergence:** Inspecting interface operational states (`show ip interface brief`), neighbor adjacencies, and dynamic routing updates (`show ip route`).
4. **Empirical Verification & Capture:** Testing cross-network reachability via ICMP ping, analyzing ARP resolutions, and archiving test captures directly within each lab folder.

---

## 📁 Lab Artifacts Structure

Every lab directory is self-contained with documentation, network diagrams, and verification evidence:

```text
networking/
├── README.md                               ← Master portfolio dashboard (this file)
├── Day-06-Static-Routing/
│   ├── README.md                           ← Objective, topology layout, IOS CLI scripts, and analysis
│   ├── topology.png                        ← Exported Packet Tracer topology diagram
│   └── ping-verification.png               ← Evidence of ICMP reachability and round-trip timing
├── Day-09-EIGRP/
│   ├── README.md
│   ├── topology.png
│   └── ping-verification.png
└── ... (Labs 01 through 30)
```

---

## 🛠️ Lab Environment & Tools

- **Simulation Platform:** [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) 8.x+
- **Hardware Emulation:** Cisco 2900 / 1941 ISR Routers, Catalyst 2960 Switches, Cisco ASA 5505 Firewalls
- **Configuration Interface:** Cisco IOS CLI (`enable`, `configure terminal`, protocol sub-modes)
- **Diagnostics:** ICMP ping, traceroute, simulation-mode PDU inspection, `show` verification commands

---

_Labs engineered and maintained by **[Jaser Halabi](https://github.com/JaserHalabi)** · Lab series commenced **2026-08-19**_
