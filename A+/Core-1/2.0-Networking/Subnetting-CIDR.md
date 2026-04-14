# 🔢 Subnetting & CIDR

**Domain:** A+ Core 1 2.0 | Network+ 1.0 + 2.0
**Professor Messer:** A+ Section 2.6 | Network+ Section 1.4
**Tags:** #subnetting #cidr #ip #comptia #aplus #networkplus

---

## 📖 Definition
Subnetting divides a network into smaller segments. CIDR notation expresses IP addresses with their subnet mask as a prefix length.

---

## 🔑 IPv4 Classes

| Class | Range | Default Mask | Use |
|---|---|---|---|
| A | 1-126 | /8 255.0.0.0 | Large networks |
| B | 128-191 | /16 255.255.0.0 | Medium networks |
| C | 192-223 | /24 255.255.255.0 | Small networks |
| D | 224-239 | N/A | Multicast |
| E | 240-255 | N/A | Reserved |

---

## 🔑 Private IP Ranges RFC 1918

| Range | CIDR | Class |
|---|---|---|
| 10.0.0.0 to 10.255.255.255 | /8 | A |
| 172.16.0.0 to 172.31.255.255 | /12 | B |
| 192.168.0.0 to 192.168.255.255 | /16 | C |

---

## 🔑 CIDR Cheat Sheet

| CIDR | Subnet Mask | Hosts |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

---

## 🔑 Special Addresses
- 127.0.0.1 = Loopback localhost
- 169.254.x.x = APIPA no DHCP found
- 0.0.0.0 = Default route
- 255.255.255.255 = Broadcast

---

## 🧠 INTELUX Lab Connection
Your lab uses 10.100.0.0/16:
- VLAN 10 MGMT: 10.100.10.0/24 — 254 hosts
- VLAN 20 SERVICES: 10.100.20.0/24 — 254 hosts
- VLAN 30 CLIENTS: 10.100.30.0/24 — 254 hosts
- VLAN 50 STAGING: 10.100.50.0/24 — 254 hosts

This is real-world subnetting you are already doing!

---

## ⚠️ Exam Gotchas
- Hosts per subnet = 2^n - 2
- APIPA = 169.254.x.x = DHCP failed
- 127.x.x.x is always loopback
- /31 and /32 are special cases

---

## 🔗 Related Topics
- [[OSI-Model]]
- [[TCP-IP-Suite]]
- [[VLAN-Concepts]]
- [[Network-Hardware]]

---

## 📅 Last Reviewed
