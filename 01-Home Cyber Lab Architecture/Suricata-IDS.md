# 🦈 Suricata IDS — INTELUX WAN Monitoring

**Updated:** 2026-04-05
**Status:** Active — EVE JSON pipeline partially built
**Host:** pfSense WAN interface

---

## Overview

Suricata is deployed on the pfSense WAN interface as the perimeter intrusion detection system. It monitors all inbound and outbound WAN traffic against the ETOpen ruleset and generates EVE JSON logs that feed into the Wazuh SIEM pipeline.

---

## Deployment

| Field | Value |
|---|---|
| Host | pfSense (FW-01, VM 100 on HV-01) |
| Interface | WAN |
| Ruleset | ETOpen (Emerging Threats Open) |
| Log format | EVE JSON |
| Status | Active — rules loaded |

---

## EVE JSON → Wazuh Pipeline

```
pfSense WAN
    │
    ▼
Suricata EVE JSON logs
    │
    ▼
rsyslog (forwarding to SRV-01)
    │
    ▼
/var/log/suricata-pfsense.log (mounted into Wazuh container)
    │
    ▼
Wazuh logcollector (analyzing file)
    │
    ▼
Wazuh indexer → dashboard
```

---

## Pipeline Status

| Step | Status |
|---|---|
| Suricata on pfSense WAN | ✅ Active |
| ETOpen rules loaded | ✅ Active |
| EVE JSON generation | ✅ Active |
| rsyslog forwarding to SRV-01 | ✅ Active |
| Log file on SRV-01 | ✅ Present |
| Wazuh logcollector analyzing | ✅ Confirmed |
| `rule.groups: suricata` in dashboard | ❌ No results |

---

## Open Issue — INC-004

**Problem:** Wazuh logcollector confirms it is reading `/var/log/suricata-pfsense.log` but `rule.groups: suricata` filter in the dashboard returns no results.

**Suspected root cause:** rsyslog is wrapping EVE JSON in a syslog envelope (timestamp + hostname prefix) before writing to file. Wazuh's built-in Suricata decoder expects raw EVE JSON — the syslog wrapper prevents correct rule matching.

**Next steps:**
- Option A: Strip syslog wrapper — configure rsyslog to write raw EVE JSON only
- Option B: Write a custom Wazuh decoder that handles the syslog-wrapped EVE JSON format

**Status:** Open — see [[Incidents-And-Lessons]] INC-004

---

## Installation Notes

- Hardware offloading required a reboot during initial Suricata install on pfSense
- ETOpen rules downloaded and applied post-reboot
- WAN interface confirmed as monitoring interface

---

## Related Notes
- [[pfSense-Firewall]]
- [[Wazuh-SIEM]]
- [[Incidents-And-Lessons]]
- [[Multi-Tiered-Defensive-Architecture]]

---
## 📚 Study Connections
| Lab Concept | Exam Topic |
|---|---|
| Suricata as IDS on WAN | [[Network-Security-Concepts]] |
| IDS vs IPS distinction | [[Network-Security-Concepts]] |
| ETOpen ruleset | [[Attack-Types]] |
| EVE JSON log pipeline | [[Net-3.0-Network-Operations-Hub]] |
| Syslog port 514 UDP | [[Ports-Protocols]] |
| Perimeter detection layer | [[Net-4.0-Network-Security-Hub]] |
| Suricata as detective control | [[Network-Security-Concepts]] |
