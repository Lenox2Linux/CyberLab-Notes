# 🌐 TCP/IP Suite

**Domain:** A+ Core 1 2.0 | Network+ 1.0
**Professor Messer:** A+ Section 2.1 | Network+ Section 1.1
**Tags:** #tcp #ip #udp #comptia #aplus #networkplus

---

## 📖 Definition
TCP/IP is the foundational protocol suite of the internet. It maps to the OSI model but uses 4 layers instead of 7.

---

## 🔑 TCP/IP vs OSI Mapping

| TCP/IP Layer | OSI Equivalent | Protocols |
|---|---|---|
| Application | Layers 5, 6, 7 | HTTP, FTP, DNS, SMTP, DHCP |
| Transport | Layer 4 | TCP, UDP |
| Internet | Layer 3 | IP, ICMP, ARP |
| Network Access | Layers 1, 2 | Ethernet, Wi-Fi, MAC |

---

## 🔑 TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | No guarantee |
| Speed | Slower | Faster |
| Use case | Web, email, file transfer | Streaming, DNS, VoIP |
| Handshake | 3-way SYN SYN-ACK ACK | None |

---

## 🔑 TCP 3-Way Handshake
1. Client → Server: SYN
2. Server → Client: SYN-ACK
3. Client → Server: ACK

---

## 🔑 Key Protocols

| Protocol | Purpose | Layer |
|---|---|---|
| IP | Addressing and routing | Internet |
| ICMP | Error reporting, ping | Internet |
| ARP | Resolves IP to MAC | Network Access |
| TCP | Reliable transport | Transport |
| UDP | Fast transport | Transport |
| DNS | Name to IP resolution | Application |
| DHCP | Automatic IP assignment | Application |

---

## ⚠️ Exam Gotchas
- ARP resolves IP to MAC not the other way
- ICMP is used by ping and traceroute
- DNS uses UDP for queries, TCP for zone transfers

---

## 🔗 Related Topics
- [[OSI-Model]]
- [[Ports-Protocols]]
- [[Subnetting-CIDR]]

---

## 📅 Last Reviewed
