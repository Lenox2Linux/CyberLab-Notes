# 🔴 Isolated Zone — VLAN 50 STAGING / VLAN 60 DMZ

**Updated:** 2026-04-05

---

## Overview

The Isolated Zone contains all untrusted or adversarial systems. No Wazuh agents are deployed here — this is intentional and documented in the asset inventory.

---

## VLAN 50 — STAGING (Red Team)

| Asset  | OS        | Role                         |
| ------ | --------- | ---------------------------- |
| RED-01 | Parrot OS | Primary red team ops machine |
| RED-02 | TBD       | Secondary (planned)          |

### RED-01 Hardware Details
- **Model:** MacBook Pro (2012)
- **User:** jcarter
- **CPU:** Intel HD 3000 (SNB GT2)
- **RAM:** 7.8GB
- **Battery:** Degraded — replacement ordered
- **Fan control:** macfanctld installed
- **Thermal repaste:** Planned post battery replacement
- **APT repos:** Accessible post-firewall fix (2026-04-02)

### RED-01 Internet Fix (2026-04-02)
- **Root cause:** pfSense STAGING rule order — Block Lab_Subnets rule was above ICMP/egress allow rules
- **Fix:** Reordered rules. Internet C2 alt rule re-enabled
- **Lab isolation:** Intact

---

## VLAN 60 — DMZ (Planned)

| Asset  | Role                             |
| ------ | -------------------------------- |
| WEB-01 | Web server — Kill Chain B target |

**Status:** Not yet deployed. Requires pfSense VLAN 60 config + SW-01 trunk + WEB-01 VM build.

---

## Firewall Rules (STAGING)

- Outbound internet: **Allowed** (C2 simulation)
- Access to CLIENTS (VLAN 30): **Controlled** — Kill Chain A attack path
- Access to SERVICES (VLAN 20): **Blocked** (except authorized pentest scope)
- Access to MGMT (VLAN 10): **Blocked**

---

## Active Operations

### Kill Chain A — In Progress
- **From:** RED-01 (10.100.50.x)
- **Target:** WKS-03 (10.100.30.x)
- **Methodology:** Black box
- **Current step:** nmap SYN scan — `-Pn` flag required (WKS-03 not responding to ping)
- **Out of scope:** WKS-04

---

## Previous Isolated Zone (Phase 0)

| Old | New |
|---|---|
| Kali Linux (VirtualBox VM) | Parrot OS (bare metal MacBook Pro) |
| No network isolation | VLAN 50 fully segmented |
| No C2 capability | Internet egress allowed for C2 simulation |

---

## Related Notes
- [[Multi-Tiered-Defensive-Architecture]]
- [[Kill-Chain-A]]
- [[RED-01]]
