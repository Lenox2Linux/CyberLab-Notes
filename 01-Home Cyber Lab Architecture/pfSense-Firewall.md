# 🔥 pfSense Firewall — INTELUX-FW-01

**Updated:** 2026-04-05
**Status:** Active — VM on HV-01 (bare-metal migration planned)
**Version:** pfSense CE 2.7.2

---

## Overview

pfSense is the core firewall and router for the INTELUX lab. It handles all inter-VLAN routing, outbound NAT, DHCP, DNS forwarding, and hosts Suricata IDS on the WAN interface. Currently running as VM 100 on HV-01 — planned migration to bare-metal M72e in Phase 2.

---

## Deployment

| Field | Value |
|---|---|
| VM ID | 100 on HV-01 |
| VLAN | All — gateway for all segments |
| Version | pfSense CE 2.7.2 |
| vCPU | 2 |
| vRAM | 4 GB |
| Virtual Disk | 32 GB |
| Interfaces | vmbr0 / vmbr1 |

---

## VLAN Configuration

| VLAN | Name | Gateway | Purpose |
|---|---|---|---|
| 10 | MGMT | .1 | Management — pfSense, HV-01, ADM-01, SW-01, DC-01 |
| 20 | SERVICES | .1 | SRV-01, Docker stack, WEB-01 |
| 30 | CLIENTS | .1 | CL-01, victim workstations |
| 40 | PORTAL | .1 | Kiosk simulation |
| 50 | STAGING | .1 | Red team — RED-01 |
| 60 | DMZ | .1 | Web-facing (planned) |

---

## Firewall Rules Summary

| Rule | Action | Notes |
|---|---|---|
| PORTAL → SERVICES | Block (except TCP 443 to WEB-01) | RISK-001 mitigation — ISO 27001 A.13.1.3 |
| STAGING → internet | Allow | C2 simulation |
| STAGING → MGMT | Block | Lab isolation |
| STAGING → SERVICES | Block (except authorized pentest) | Lab isolation |
| All VLANs → internet | Allow (NAT) | Outbound NAT configured |
| Wazuh API (port 55000) | MGMT only | Locked to management VLAN |

> ⚠️ Rule order is top-down in pfSense. Always verify ordering after any change. See [[Incidents-And-Lessons]] — INC-001 root cause was incorrect rule order.

---

## DHCP

- Kea DHCP running on pfSense for all VLANs
- Static reservations for all infrastructure devices

---

## DNS

- Pi-hole on SRV-01 (VLAN 20) handles internal DNS
- pfSense DNS resolver forwards to Pi-hole
- Forced DNS rule applied — TCP + UDP (TCP-only caused issues)

---

## Suricata IDS

- Deployed on WAN interface
- ETOpen ruleset active
- EVE JSON → rsyslog → Wazuh pipeline
- See [[Suricata-IDS]] for full pipeline details

---

## Known Issues & Lessons

| Issue | Status | Notes |
|---|---|---|
| Rule order — STAGING internet broken | Resolved 2026-04-02 | Block rule was above egress allows — INC-001 |
| Forced DNS TCP-only | Resolved | Added UDP to DNS rule |

---

## Planned Migration

Phase 2: Migrate pfSense from VM (HV-01) to bare-metal on M72e.
- Onboard NIC → LAN
- Realtek USB NIC (currently on HV-01) → WAN
- Export XML config from current VM — import to bare-metal

See [[INTELUX-FW-01-M72e-Planned]].

---

## Config Backup

Step2 XML backup saved post-VLAN migration (March 30, 2026).

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[Multi-Tiered-Defensive-Architecture]]
- [[Suricata-IDS]]
- [[INTELUX-FW-01-M72e-Planned]]
- [[Incidents-And-Lessons]]
- [[RISK-001-Closed]]
