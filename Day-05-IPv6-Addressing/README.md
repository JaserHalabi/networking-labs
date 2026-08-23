# IPv6 Addressing & Subnetting

> **Lab Folder:** `Day-05-IPv6-Addressing`

---

## 🎯 Objective

Configure IPv6 global unicast and link-local addressing, enable IPv6 unicast routing on Cisco IOS, and verify end-to-end connectivity across subnets.

---

## 📖 Theoretical Fundamentals

### What is IPv6? (Beginner Summary)
- **Why do we need IPv6?** The internet ran out of IPv4 addresses. IPv4 is 32 bits (~4.3 billion addresses), while IPv6 is **128 bits** (giving virtually unlimited addresses).
- **How is it written?** Instead of 4 numbers separated by dots (like `192.168.1.1`), IPv6 is written in hexadecimal using 8 groups separated by colons (like `2001:db8:acad:1::1`).
- **Quick Comparison:**
  - **IPv4:** 32 bits · Dotted-decimal (`0` to `255`) · Uses ARP & Broadcast.
  - **IPv6:** 128 bits · Hexadecimal (`0-9` and `A-F`) · Uses Neighbor Discovery & Multicast (no Broadcast).

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

## 📝 Notes & Reflection

- Successfully configured two separate IPv6 subnets on a Cisco 1941 router and verified full end-to-end communication with ICMPv6 echo replies.
- Packet Tracer version used: **8.x / 9.x**
- Date completed: **2026-08-23**

---

_Back to [Portfolio Root](../README.md)_
