# IPv6 Addressing & Subnetting

> **Lab Folder:** `Day-05-IPv6-Addressing`

---

## 🎯 Objective

Configure IPv6 global unicast and link-local addressing, enable IPv6 unicast routing on Cisco IOS, and verify end-to-end connectivity across subnets.

---

## 📖 Theoretical Fundamentals

### 1. IPv4 vs. IPv6 Key Differences

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Length** | 32 bits (4 bytes) | **128 bits** (16 bytes) |
| **Notation** | Dotted decimal (e.g., `192.168.1.1`) | Hexadecimal hextets (e.g., `2001:db8:acad:1::1`) |
| **Total Address Space** | $\approx 4.29 \times 10^9$ ($2^{32}$) | $\approx 3.4 \times 10^{38}$ ($2^{128}$) |
| **Subnet Mask Format** | Dotted decimal (e.g., `255.255.255.0`) or `/24` | Prefix length only (e.g., `/64`) |
| **Address Resolution** | ARP (Address Resolution Protocol - Broadcast) | NDP (Neighbor Discovery Protocol - Multicast) |
| **Packet Types** | Unicast, Multicast, Broadcast | Unicast, Multicast, **Anycast** (No Broadcast) |
| **NAT Necessity** | Mandatory for scaling due to exhaustion | Not required (end-to-end global addressing) |
| **Auto-Configuration** | DHCPv4 or Manual | SLAAC, DHCPv6 (Stateless / Stateful), or Manual |

---

## 🖼️ Topology & Lab Walkthrough

### Topology Overview
The topology consists of a Cisco 1941 Router interconnecting two separate IPv6 subnets through 2960 switches to end PCs:

![Topology Diagram](topology.png)

* **Subnet A (LAN 1):** `2001:db8:acad:1::/64`
  * Router `GigabitEthernet0/0`: `2001:db8:acad:1::1/64`
  * Host `PC0`: `2001:db8:acad:1::10/64` (Gateway: `2001:db8:acad:1::1`)
* **Subnet B (LAN 2):** `2001:db8:acad:2::/64`
  * Router `GigabitEthernet0/1`: `2001:db8:acad:2::1/64`
  * Host `PC1`: `2001:db8:acad:2::10/64` (Gateway: `2001:db8:acad:2::1`)

---

## 🖥️ Clean Cisco IOS Configuration

```bash
! Enter privileged EXEC mode and configuration mode
enable
configure terminal

! Enable IPv6 routing on the router (Mandatory for routing IPv6 packets)
ipv6 unicast-routing

! Configure Interface GigabitEthernet0/0 (Subnet 1 - Left LAN)
interface GigabitEthernet0/0
 description LAN-1-Segment
 ipv6 address 2001:db8:acad:1::1/64
 no shutdown
exit

! Configure Interface GigabitEthernet0/1 (Subnet 2 - Right LAN)
interface GigabitEthernet0/1
 description LAN-2-Segment
 ipv6 address 2001:db8:acad:2::1/64
 no shutdown
exit

! Return to privileged EXEC and save configuration
end
copy running-config startup-config
```

---

## ✅ Verification & Connectivity

### Verification Commands

| Command | Purpose |
| :--- | :--- |
| `show ipv6 interface brief` | Verify IPv6 global unicast and link-local addresses and interface status (Up/Up) |
| `show ipv6 route` | Display the IPv6 routing table showing connected (`C`) and local (`L`) prefixes |
| `ping <ipv6-address>` | Test ICMPv6 connectivity |

### End-to-End Ping Test
Ping from `PC0` (`2001:db8:acad:1::10`) across the router to `PC1` (`2001:db8:acad:2::10`):

![Ping Verification](ping-verification.png)

```text
C:\>ping 2001:db8:acad:2::10

Pinging 2001:db8:acad:2::10 with 32 bytes of data:

Reply from 2001:DB8:ACAD:2::10: bytes=32 time<1ms TTL=128
Reply from 2001:DB8:ACAD:2::10: bytes=32 time=3ms TTL=128
Reply from 2001:DB8:ACAD:2::10: bytes=32 time<1ms TTL=128
Reply from 2001:DB8:ACAD:2::10: bytes=32 time=4ms TTL=128

Ping statistics for 2001:DB8:ACAD:2::10:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
```

---

## 📝 Notes & Key Takeaways

- **`ipv6 unicast-routing`**: By default, Cisco routers do not forward IPv6 packets. Running `ipv6 unicast-routing` in global configuration mode enables IPv6 routing and allows the router to send ICMPv6 Router Advertisements (RA).
- **Link-Local Addresses (`FE80::/10`)**: Automatically generated on every IPv6-enabled interface, used for local link communication (NDP, next-hop routing).
- Packet Tracer version used: **8.x / 9.x**
- Date completed: **2026-08-23**

---

_Back to [Portfolio Root](../README.md)_
