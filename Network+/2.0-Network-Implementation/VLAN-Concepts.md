# 🔀 VLAN Concepts

**Domain:** Network+ 2.0
**Professor Messer:** Network+ Section 2.3
**Tags:** #vlan #switching #networking #comptia #networkplus

---

## 📖 Definition
A VLAN logically segments a physical network at Layer 2, creating separate broadcast domains without separate physical infrastructure.

---

## 🔑 Key Concepts
- VLANs operate at Layer 2 (Data Link)
- Each VLAN = separate broadcast domain
- Traffic between VLANs requires a Layer 3 device
- VLANs are configured on managed switches
- Identified by VLAN ID (1-4094)

---

## 🔑 VLAN Types

| Type | Description |
|---|---|
| Data VLAN | Carries user traffic |
| Voice VLAN | Dedicated for VoIP |
| Management VLAN | For managing network devices |
| Native VLAN | Untagged traffic on trunk |

---

## 🔑 Trunk vs Access Ports

| Port Type | Description | Use |
|---|---|---|
| Access Port | Belongs to one VLAN | End devices |
| Trunk Port | Carries multiple VLANs | Switch-to-switch |

---

## 🔑 802.1Q Tagging
- Standard for VLAN tagging on trunk links
- Adds a 4-byte tag to the Ethernet frame

---

## 🧠 INTELUX Lab Connection

| VLAN | ID | Subnet | Purpose |
|---|---|---|---|
| MGMT | 10 | 10.100.10.0/24 | Management |
| SERVICES | 20 | 10.100.20.0/24 | Servers |
| CLIENTS | 30 | 10.100.30.0/24 | Workstations |
| KIOSK | 40 | 10.100.40.0/24 | Kiosk VMs |
| STAGING | 50 | 10.100.50.0/24 | Red team |
| DMZ | 60 | 10.100.60.0/24 | Public-facing (pending) |

Inter-VLAN routing done by pfSense = router-on-a-stick

---

## ⚠️ Exam Gotchas
- Default VLAN is VLAN 1 — best practice is not to use it
- Native VLAN traffic is untagged — security risk
- VLAN hopping exploits trunk misconfiguration
- VLANs provide segmentation not encryption

---

## 🔗 Related Topics
- [[Network-Hardware]]
- [[Subnetting-CIDR]]
- [[Network-Security-Concepts]]
- [[Routing-Concepts]]

---

## 📅 Last Reviewed
