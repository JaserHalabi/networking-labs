# RIP (Routing Information Protocol)

---

## 🎯 Objective

Connect 3 routers, 3 switches, and PCs together, and configure dynamic routing using RIP so all devices across different networks can communicate.

---

## 📖 Theoretical Fundamentals

### What is RIP?
- **What is RIP?** RIP stands for Routing Information Protocol. It is used in small to medium-sized networks so routers can automatically learn and share routes with each other.
- **How does it choose paths?** It finds the best path based on the number of **hops** (the number of routers a packet travels through). The path with the fewest hops is chosen.
- **Hop Limit:** The maximum hop count is 15 hops
- **Important Commands Used:**
  - `router rip` — Enters RIP routing configuration mode on the router.
  - `network <network-address>` — Tells the router which directly connected networks to advertise to neighbor routers.

---

## 🖼️ Topology & Lab Walkthrough

### Topology Overview
The network connects 3 local LANs across 3 routers using serial links:

![Topology Diagram](topology.png)

* **LAN 1 (Left):** `192.168.1.0/24` (Router 0 `Fa0/0`: `192.168.1.1`, PCs: `192.168.1.2`, `192.168.1.3`)
* **WAN 1 (Link R0-R1):** `10.0.0.0/30` (Router 0 `Se2/0`: `10.0.0.1`, Router 1 `Se3/0`: `10.0.0.2`)
* **LAN 2 (Middle):** `192.168.2.0/24` (Router 1 `Fa0/0`: `192.168.2.1`, PCs: `192.168.2.2`, `192.168.2.3`)
* **WAN 2 (Link R1-R2):** `20.0.0.0/30` (Router 1 `Se2/0`: `20.0.0.1`, Router 2 `Se2/0`: `20.0.0.2`)
* **LAN 3 (Right):** `192.168.3.0/24` (Router 2 `Fa0/0`: `192.168.3.1`, PCs: `192.168.3.2`, `192.168.3.3`)

---

## 🖥️ Clean Cisco IOS Configuration

### Router 0 (Left Router)

```bash
enable
configure terminal

! 1. Configure Interfaces
interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit

interface Serial2/0
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit

! 2. Configure Dynamic RIP Routing
router rip
 network 192.168.1.0
 network 10.0.0.0
exit

! 3. Save Configuration
end
copy running-config startup-config
```

---

### Router 1 (Middle Router)

```bash
enable
configure terminal

! 1. Configure Interfaces
interface FastEthernet0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown
exit

interface Serial3/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown
exit

interface Serial2/0
 ip address 20.0.0.1 255.255.255.252
 no shutdown
exit

! 2. Configure Dynamic RIP Routing
router rip
 network 192.168.2.0
 network 10.0.0.0
 network 20.0.0.0
exit

! 3. Save Configuration
end
copy running-config startup-config
```

---

### Router 2 (Right Router)

```bash
enable
configure terminal

! 1. Configure Interfaces
interface FastEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown
exit

interface Serial2/0
 ip address 20.0.0.2 255.255.255.252
 no shutdown
exit

! 2. Configure Dynamic RIP Routing
router rip
 network 192.168.3.0
 network 20.0.0.0
exit

! 3. Save Configuration
end
copy running-config startup-config
```

---

## ✅ Verification & Connectivity

### End-to-End Ping Test
Testing connectivity from a PC across the routers to `PC2` (`192.168.2.2`):

![Ping Verification](ping-verification.png)

```text
C:\>ping 192.168.2.2

Pinging 192.168.2.2 with 32 bytes of data:

Request timed out.
Reply from 192.168.2.2: bytes=32 time=14ms TTL=126
Reply from 192.168.2.2: bytes=32 time=13ms TTL=126
Reply from 192.168.2.2: bytes=32 time=9ms TTL=126

Ping statistics for 192.168.2.2:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 9ms, Maximum = 14ms, Average = 12ms
```

> **Note on Initial Timeout:** The first ping packet times out because of the initial ARP request resolving the destination MAC address. After that, subsequent packets succeed!

---

## 📝 Notes & Reflection

- First time configuring RIP dynamic routing between 3 routers.
- Instead of manually writing every single route like static routing, we just enable `router rip` and type `network` with the directly connected IP networks.
- The routers automatically share their routes with each other using hop count.
- Packet Tracer version used: **8.x / 9.x**
- Date completed: **2026-08-24**

---

_Back to [Portfolio Root](../README.md)_
