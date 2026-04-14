# 🔒 Network Security Concepts

**Domain:** A+ Core 2 2.0 | Network+ 4.0
**Professor Messer:** A+ Section 2.1 | Network+ Section 4.1
**Tags:** #security #networking #comptia #aplus #networkplus

---

## 📖 Definition
Network security involves protecting infrastructure, data, and resources from unauthorized access, misuse, or attacks.

---

## 🔑 CIA Triad

| Concept | Definition | Example |
|---|---|---|
| Confidentiality | Only authorized access | Encryption, VPN |
| Integrity | Data not tampered with | Hashing, checksums |
| Availability | Systems accessible when needed | Redundancy, backups |

---

## 🔑 AAA Framework
- **Authentication** — Who are you?
- **Authorization** — What can you do?
- **Accounting** — What did you do?

---

## 🔑 Security Controls

| Type | Description | Example |
|---|---|---|
| Preventive | Stop attacks | Firewall, ACL |
| Detective | Identify attacks | IDS, SIEM, logs |
| Corrective | Respond after attack | Patch, restore backup |
| Deterrent | Discourage attacks | Warning banners |

---

## 🔑 Network Segmentation
- **VLANs** — Logical separation at Layer 2
- **DMZ** — Isolated zone for public-facing services
- **Zero Trust** — Never trust, always verify
- **Least Privilege** — Only access what is needed

---

## 🧠 INTELUX Lab Connection
- pfSense firewall rules = Preventive controls
- Suricata IDS = Detective controls
- Wazuh SIEM = Detective + accounting
- VLANs 10/20/30/40/50 = Network segmentation
- VLAN 60 DMZ (pending) = DMZ architecture

---

## ⚠️ Exam Gotchas
- IDS = detects and alerts only
- IPS = detects AND blocks
- Firewall = Layer 3/4 filtering
- WAF = Layer 7
- UTM = all-in-one security appliance

---

## 🔗 Related Topics
- [[Firewalls-ACLs]]
- [[IDS-IPS]]
- [[VPN-Concepts]]
- [[Attack-Types]]
- [[VLAN-Concepts]]

---

## 📅 Last Reviewed
