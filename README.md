# Cisco Networking Engineering Labs

[![Packet Tracer](https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer%208.x-blue?style=flat-square)](https://www.netacad.com/courses/packet-tracer)
[![Cisco IOS](https://img.shields.io/badge/CLI-Cisco%20IOS-informational?style=flat-square)](https://www.cisco.com)
[![Status](https://img.shields.io/badge/Labs%20Completed-10%20Verified-success?style=flat-square)](#lab-execution-matrix)
[![Engineer](https://img.shields.io/badge/Engineer-Jaser%20Halabi-lightgrey?style=flat-square&logo=github)](https://github.com/JaserHalabi)

> A practical portfolio of enterprise networking labs, Cisco IOS CLI configurations, routing and switching architectures, and empirical protocol verifications built and tested in **Cisco Packet Tracer**.

---

## Overview

This repository documents hands-on network implementations, architectural designs, and protocol validations. Rather than theoretical notes, every lab represents a functional network scenario featuring custom topology design, router and switch configuration via the Cisco IOS command-line interface (CLI), and end-to-end data plane testing.

### Core Engineering Competencies

- **Topology Engineering:** Multi-router, multi-switch network architectures with IPv4 and IPv6 subnetting schemes, including point-to-point /30 serial links.
- **Cisco IOS CLI Provisioning:** Production-grade configuration scripts for enterprise routers, Catalyst switches, and security appliances.
- **Routing and Switching:** Deployments of Static Routing, RIP v2, EIGRP, OSPF single/multi-area, VLAN segmentation (802.1Q), Inter-VLAN routing, and Spanning Tree Protocol (STP).
- **Device Hardening:** Security controls including enable secret hashing (MD5), service password-encryption, console and VTY transport restrictions, and login banners.
- **Verification and Diagnostics:** Data plane validation via ICMP reachability analysis, round-trip timing, ARP table inspection, and IOS state inspection (`show ip route`, `show ip protocols`, `show running-config`).

---

## Featured Implementations

Key hands-on labs completed and verified with topologies, configuration scripts, and connectivity captures:

| Lab | Engineering Focus | Key IOS Highlights | Verification Capture |
|---|---|---|---|
| **[OSPF Single-Area Routing](./OSPF-Routing/)** | Single-area link-state routing, neighbor adjacencies, and ECMP load balancing | `router ospf 1`, `network ... area 0` | [Topology & Ping Capture](./OSPF-Routing/ping-verification.png) |
| **[Enterprise Multi-Router RIP Network](./Multi-Router-RIP-Routing/)** | 8-router circular backbone network with 14 subnets and multi-hop metric convergence | `router rip`, `version 2`, `network`, `no auto-summary` | [Topology & Ping Capture](./Multi-Router-RIP-Routing/ping-verification.png) |
| **[EIGRP Dynamic Routing](./EIGRP-Routing/)** | Dynamic routing across dual routers and multiple LAN subnets | `router eigrp <AS>`, `network <net> <wildcard>`, `no auto-summary` | [Topology & Ping Capture](./EIGRP-Routing/ping-verification.png) |
| **[RIP Dynamic Routing](./RIP-Routing/)** | Distance-vector protocol deployment and metric convergence | `router rip`, `version 2`, `network` statements | [Topology & Ping Capture](./RIP-Routing/ping-verification.png) |
| **[Static Routing over Serial WAN](./Static-Routing/)** | Point-to-point /30 serial link interconnecting isolated subnets | `interface Serial0/3/0`, `ip route <dest> <mask> <next-hop>` | [Topology & Ping Capture](./Static-Routing/ping-verification.png) |
| **[IPv6 Addressing & Routing](./IPv6-Addressing/)** | Dual-stack GUA configuration and neighbor discovery | `ipv6 address <GUA>/64`, `ipv6 enable` | [Topology & Ping Capture](./IPv6-Addressing/ping-verification.png) |
| **[Switch Hardening & Device Security](./Basic-Network-Security/)** | Layer 2 switch hardening and access control | `enable secret`, `service password-encryption`, `line vty 0 15` | [Verification Show Run](./Basic-Network-Security/verification-show-run.png) |

---

## Lab Execution Matrix

| # | Lab Module | Architectural Focus | Status | Completed |
|---|---|---|:---:|:---:|
| 01 | [Hardware Identification & Device Interfacing](./Networking-Devices/) | Interface layout and role definition for routers, switches, and firewalls | Complete | 2026-08-19 |
| 02 | [Physical Media & Cabling Standards](./Connecting-Devices/) | Fiber (Single/Multi-Mode), Crossover, and Straight-Through deployment | Complete | 2026-08-19 |
| 03 | [OSI Protocol Analysis & PDU Inspection](./OSI-Model/) | Packet inspection and protocol analysis across OSI layers | Complete | 2026-08-19 |
| 04 | [Switch Hardening & Line Security](./Basic-Network-Security/) | Cisco switch security, secret hashing, and console/VTY access control | Complete | 2026-08-19 |
| 05 | [IPv6 Dual-Stack Addressing](./IPv6-Addressing/) | Global Unicast Addressing (GUA) and IPv6 neighbor discovery | Complete | 2026-08-23 |
| 06 | [Dual-Router Static Routing over Serial WAN](./Static-Routing/) | Point-to-point /30 serial WAN links and static routing tables | Complete | 2026-08-24 |
| 07 | [Dynamic Routing with RIP v2](./RIP-Routing/) | Distance-vector protocol deployment and convergence testing | Complete | 2026-08-24 |
| 08 | [Enterprise Routing with EIGRP](./EIGRP-Routing/) | Autonomous system routing, composite metric tuning, and convergence | Complete | 2026-08-25 |
| 09 | [Enterprise Multi-Router RIP Network](./Multi-Router-RIP-Routing/) | 8-router circular backbone, 14 subnets, and multi-hop metric convergence | Complete | 2026-10-07 |
| 10 | [OSPF Single-Area Routing](./OSPF-Routing/) | Link-state routing, Area 0 adjacency, and ECMP multi-path convergence | Complete | 2026-10-13 |

> *Additional lab implementations will be analyzed, documented, and published here as new topologies and configurations are completed.*

---

## Environment & Tooling

- **Simulation Platform:** [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) 8.x+
- **Emulated Hardware:** Cisco 2900 / 1941 ISR Routers, Catalyst 2960 Switches, Cisco ASA 5505 Firewalls
- **Configuration Interface:** Cisco IOS CLI
- **Diagnostics:** ICMP ping, traceroute, simulation-mode PDU packet tracing, IOS show commands

---

_Maintained by **[Jaser Halabi](https://github.com/JaserHalabi)**_
