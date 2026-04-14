# 🗺️ Kill Chain B — Portal Kiosk Pivot

**Updated:** 2026-04-05
**Status:** Planned — prerequisites not yet met

---

![[Kill-Chain-B-Flow.png]]

---

## Context

Attack flow diagram for Kill Chain B — planned portal kiosk pivot exercise. Shows the attack path from KSK-01 (VLAN 40 PORTAL) through the TCP 443 pinhole to WEB-01 (VLAN 20 SERVICES), then pivoting to DC-01 as the crown jewel target. Also documents the RISK-001 pfSense firewall mitigation and blue team detection opportunities via Wazuh. Exercise is blocked pending VLAN 60 DMZ configuration and WEB-01 deployment.

---

## Related Notes

- [[Kill-Chain-B-Flow]]
- [[RISK-001-Closed]]
- [[INTELUX-DC-01]]
- [[pfSense-Firewall]]
- [[Diagrams-Index]]

---
## 📚 Study Connections
| Lab Concept | Exam Topic |
|---|---|
| External attacker pivot scenario | [[Attack-Types]] |
| TCP 443 pinhole firewall rule | [[Network-Security-Concepts]] |
| VLAN 40 PORTAL → VLAN 20 SERVICES path | [[VLAN-Concepts]] |
| DC-01 as crown jewel target | [[1.0-Operating-Systems-Hub]] |
| RISK-001 mitigation as defense control | [[Network-Security-Concepts]] |
| DMZ architecture (VLAN 60) | [[Net-4.0-Network-Security-Hub]] |
| Wazuh detection opportunities | [[Network-Security-Concepts]] |
| Defense-in-depth layered controls | [[Net-4.0-Network-Security-Hub]] |
| Pivot attack technique | [[Attack-Types]] |
| Kill chain framework | [[Net-4.0-Network-Security-Hub]] |
