# 🛡️ Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation

**Updated:** 2026-04-05
**Status:** Live — Phase 2 Active Defense

---

## Architecture Philosophy

INTELUX is modeled after a real enterprise SOC/NOC environment. The design follows a **defense-in-depth** model with:

- Network segmentation via VLANs (replacing the old flat 192.168.1.x network)
- East-west traffic control between VLANs via pfSense firewall rules
- SIEM visibility on all non-red-team VLANs
- Dedicated red team VLAN (STAGING/50) isolated from production
- GRC documentation aligned to ISO 27001

---

## Defense Layers

### Layer 1 — Perimeter (WAN)
- **Suricata IDS** on pfSense WAN interface
- ETOpen ruleset active
- EVE JSON logs → rsyslog (port 5140) → `/var/log/suricata-pfsense.log` → Wazuh pipeline
- **Status:** Deployed. EVE JSON parsing issue pending (syslog wrapper format blocking `rule.groups: suricata` filter in dashboard)

### Layer 2 — Network Segmentation
- 6 VLANs enforced via pfSense + SW-01
- Inter-VLAN routing controlled — no implicit trust between segments
- **RISK-001 CLOSED (2026-03-31):** PORTAL→SERVICES lateral movement mitigated
  - TCP 443 pinhole to WEB-01 (10.100.20.103) only
  - Rest of SERVICES blocked from PORTAL
  - ISO 27001 A.13.1.3 satisfied

### Layer 3 — Host-Based Detection
- Wazuh agents on: ADM-01 (T2/008), SRV-01 (SV/009), HV-01 (290/010), CL-01 (190/011)
- WKS-01 ossec.conf manager IP update pending (still pointing to old IP)
- No agents on RED-01 or RED-02 (intentional — documented in inventory)

### Layer 4 — Application Security
- Caddy reverse proxy with local TLS (`local_certs`) for all `*.intelux.local` subdomains
- Wazuh CA cert mounted via `tls_trust_pool file` (replaced `tls_insecure_skip_verify`)
- Vaultwarden MFA enabled

### Layer 5 — Identity & Access (Planned)
- DC-01 pending deploy (10.100.20.102, VLAN 20)
- Will provide AD DS, DNS, Group Policy for INTELUX domain

---

## Isolation Model

```
[WAN]
  │
[pfSense + Suricata]
  │
  ├── VLAN 10 MGMT      → pfSense, HV-01, ADM-01, SW-01
  ├── VLAN 20 SERVICES  → SRV-01, DC-01, WEB-01
  ├── VLAN 30 CLIENTS   → CL-01, WKS-01–04
  ├── VLAN 40 PORTAL    → INTELUX-KSK-01 (kiosk)
  ├── VLAN 50 STAGING   → RED-01, RED-02 (no Wazuh agents)
  └── VLAN 60 DMZ       → WEB-01 (planned)
```

---

## Kill Chain Scenarios

### Kill Chain A — STAGING Insider Threat
- Attacker: RED-01 (10.100.50.100, VLAN 50)
- Target: WKS-03 (10.100.30.11, VLAN 30)
- Method: Black box — nmap SYN scan (`-Pn` required, WKS-03 blocks ping)
- Status: **In progress**

### Kill Chain B — PORTAL Kiosk Pivot (Planned)
- Attacker: INTELUX-KSK-01 (10.100.40.101, VLAN 40)
- Path: TCP 443 pinhole → WEB-01 (10.100.20.103) → DC-01 crown jewel
- Prerequisite: VLAN 60 DMZ live, WEB-01 deployed
- Status: **Blocked — awaiting VLAN 60**

---

## Previous Architecture (Phase 0 Reference)

| Old | New |
|---|---|
| Flat 192.168.1.x | 10.100.x.x VLAN-segmented |
| Oracle VirtualBox | Proxmox (HV-01, CL-01) |
| MacBook Air (2020) | SRV-01 (Mac Mini, Ubuntu/Docker) |
| MacBook Pro (2012) | RED-01 (MacBook Pro, Parrot OS) |
| TP-Link AX50 | pfSense on M72e (current VM, bare-metal planned) |
| No SIEM | Wazuh v4.14.3 |
| No IDS | Suricata on pfSense WAN |

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[pfSense-Firewall]]
- [[Wazuh-SIEM]]
- [[Suricata-IDS]]
- [[RISK-001-Closed]]
