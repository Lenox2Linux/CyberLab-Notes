# 🏗️ INTELUX Lab Architecture Overview

**Vault Last Updated:** 2026-04-05
**Lab Name:** INTELUX Systems, Inc.
**Internal Domain:** `intelux.local`
**Owner:** Raynard A. Porter (`aredeebee`)
**Status:** Active — Sprint in progress

---

## Evolution Summary

| Phase | Period | Description |
|---|---|---|
| Phase 0 | Early 2026 | Flat network, single subnet 192.168.1.x, VirtualBox-based |
| Phase 1 | March 2026 | Full VLAN migration to 10.100.x.x, Proxmox hypervisors, pfSense firewall |
| Phase 2 | April 2026+ | Active Defense — Suricata IDS, Wazuh SIEM, GRC documentation, Red Team ops |

---

## Current Network Architecture

### VLAN Topology

| VLAN | Name | Subnet | Purpose |
|---|---|---|---|
| 10 | MGMT | 10.100.10.0/24 | Management — pfSense, HV-01, ADM-01, SW-01 |
| 20 | SERVICES | 10.100.20.0/24 | SRV-01, Wazuh, Caddy, DC-01 (planned) |
| 30 | CLIENTS | 10.100.30.0/24 | CL-01, workstations WKS-01 through WKS-04 |
| 40 | PORTAL | 10.100.40.0/24 | Kiosk simulation — INTELUX-KSK-01 |
| 50 | STAGING | 10.100.50.0/24 | Red Team — RED-01, RED-02 |
| 60 | DMZ | 10.100.60.0/24 | Web-facing — WEB-01 (planned) |

---

## Core Services (Live)

| Service             | Host               |
| ------------------- | ------------------ |
| Wazuh SIEM          | SRV-01             |
| Caddy Reverse Proxy | SRV-01             |
| Pi-hole DNS         | SRV-01             |
| Nextcloud           | SRV-01             |
| Vaultwarden         | SRV-01             |
| Suricata IDS        | pfSense WAN        |
| Tailscale           | SRV-01 / ts-sub-01 |

---

## Remote Access

- **Primary:** Tailscale subnet router (`ts-sub-01`) advertising `10.100.0.0/16`
- **Admin rule:** Disable WiFi on ADM-01 before connecting ethernet during lab sessions (dual-homing risk)
- **Wazuh API:** Port 55000 locked to MGMT VLAN only

---

## Planned / In Progress

- [ ] DC-01 deploy (VM 101, 10.100.20.x, VLAN 20)
- [ ] VLAN 60 DMZ — pfSense + SW-01 + WEB-01 (10.100.60.x)
- [ ] East-west Docker isolation on SRV-01 (blocked — restore port bindings first)
- [ ] pfSense migration to M72e bare-metal
- [ ] Wazuh expansion post DC-01
- [ ] M900 Tiny home server (Jellyfin, Immich, Nextcloud — Tailscale-only)

---

## Related Notes

- [[(Phase 0) Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation]]
- [[(Phase 0) Isolated Zone]]
- [[(Phase 0) Trusted Zone]]
- [[pfSense-Firewall]]
- [[SRV-01-Services]]
