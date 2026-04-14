# 🔧 Network Hardware

**Domain:** A+ Core 1 2.0 | Network+ 2.0
**Professor Messer:** A+ Section 2.2 | Network+ Section 2.1
**Tags:** #hardware #networking #comptia #aplus #networkplus

---

## 📖 Definition
Network hardware devices connect, route, and manage network traffic. Each device operates at a specific OSI layer.

---

## 🔑 Devices by OSI Layer

| Device | OSI Layer | Function |
|---|---|---|
| Hub | Layer 1 | Broadcasts to all ports |
| Switch | Layer 2 | Forwards by MAC address |
| Router | Layer 3 | Forwards by IP address |
| Layer 3 Switch | Layer 3 | Switch with routing |
| WAP | Layer 2 | Wireless access point |
| Firewall | Layer 3-7 | Filters by rules |
| NIC | Layer 1-2 | Network interface card |
| Modem | Layer 1 | Modulates signal |

---

## 🔑 Switch vs Hub vs Router

| Device | Collision Domain | Broadcast Domain |
|---|---|---|
| Hub | Shared | Shared |
| Switch | Per port | Shared |
| Router | Per port | Per interface |

---

## 🔑 Other Devices
- Repeater — Amplifies signal Layer 1
- Bridge — Connects two segments Layer 2
- Proxy — Acts on behalf of clients Layer 7
- Load Balancer — Distributes traffic
- IDS/IPS — Intrusion detection/prevention
- UTM — Unified Threat Management

---

## 🧠 INTELUX Lab Connection
- SW-01 Netgear = managed Layer 2/3 switch
- pfSense = router + firewall + UTM
- Suricata on pfSense = IDS/IPS

---

## ⚠️ Exam Gotchas
- Hubs create collision domains
- Switches break up collision domains not broadcast domains
- Routers break up both collision AND broadcast domains
- Managed switch can do VLANs, unmanaged cannot

---

## 🔗 Related Topics
- [[OSI-Model]]
- [[VLAN-Concepts]]
- [[Wireless-Standards]]
- [[Subnetting-CIDR]]

---

## 📅 Last Reviewed
