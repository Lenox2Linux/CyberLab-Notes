# 🏗️ INTELUX Lab Architecture Overview

**Vault Last Updated:** 2026-04-05 **Lab Name:** INTELUX Systems, Inc. **Internal Domain:** `intelux.local` **Owner:** aredeebee **Status:** Active — Sprint in progress

---

## Evolution Summary

|Phase|Period|Description|
|---|---|---|
|Phase 0|Early 2026|Flat network, single subnet, VirtualBox-based|
|Phase 1|March 2026|Full VLAN migration, Proxmox hypervisors, pfSense firewall|
|Phase 2|April 2026+|Active Defense — Suricata IDS, Wazuh SIEM, GRC documentation, Red Team ops|
|Phase 2.1|April 2026|DC-01 deployed — intelux.local domain live, WKS-03 domain joined|

---

## Current Network Architecture

### VLAN Topology

|VLAN|Name|Purpose|
|---|---|---|
|10|MGMT|pfSense, HV-01, ADM-01, SW-01, DC-01|
|20|SERVICES|SRV-01, Wazuh, Caddy, WEB-01 (planned)|
|30|CLIENTS|CL-01, WKS-03, WKS-04|
|40|PORTAL|Kiosk simulation — KSK-01 (planned)|
|50|STAGING|Red Team — RED-01, RED-02 (planned)|
|60|DMZ|Web-facing — WEB-01 (planned)|

### Confirmed Device Registry

|Device|VLAN|Role|Status|
|---|---|---|---|
|pfSense (FW-01)|10|Firewall / Router / Suricata|Active|
|HV-01 (M920q)|10|Proxmox hypervisor|Active|
|ADM-01 (T14)|10|Admin workstation|Active|
|SW-01 (GS308E)|10|Managed switch|Active|
|DC-01 (VM 103)|10|AD DS — intelux.local|✅ Active — deployed|
|SRV-01 (Mac Mini)|20|Docker services host|Active|
|WEB-01 (VM 104)|20/60|Intranet web server|Planned|
|CL-01 (M910q)|30|Proxmox hypervisor|Active|
|WKS-03 (VM 101)|30|Victim workstation — domain joined|Active|
|WKS-04 (VM 102)|30|Victim workstation|Active (powered off)|
|KSK-01 (VM 105)|40|Portal kiosk|Planned|
|RED-01 (MBP 2012)|50|Red team — Parrot OS|Active|
|RED-02 (VM 150)|50|Red team VM|Planned|

---

## Core Services (Live)

|Service|Host|Status|
|---|---|---|
|Wazuh SIEM v4.14.3|SRV-01|Active|
|Caddy Reverse Proxy|SRV-01|Active|
|Pi-hole DNS|SRV-01|Active|
|Grafana|SRV-01|Active|
|Prometheus|SRV-01|Active|
|Nextcloud|SRV-01|Active|
|Vaultwarden|SRV-01|Active|
|Uptime Kuma|SRV-01|Active|
|Suricata IDS|pfSense WAN|Active|
|Tailscale|SRV-01|Active|
|Active Directory|DC-01|✅ Active|

---

## Remote Access

- **Primary:** Tailscale subnet router advertising lab subnet
- **Admin rule:** Disable WiFi on ADM-01 before connecting ethernet during lab sessions
- **Wazuh API:** Locked to MGMT VLAN only

---

## Active / In Progress

- [x] DC-01 deployed — intelux.local domain live
- [x] WKS-03 domain joined to intelux.local
- [ ] DC-01 Wazuh agent install
- [ ] VLAN 60 DMZ — pfSense + SW-01 + WEB-01
- [ ] East-west Docker isolation on SRV-01
- [ ] pfSense migration to M72e bare-metal
- [ ] Kill Chain A exercise — recon phase in progress
- [ ] M900 Tiny home server

---

## Related Notes

- [[Multi-Tiered-Defensive-Architecture]]
- [[Trusted-Zone]]
- [[Isolated-Zone]]
- [[VM-Registry]]
- [[INTELUX-DC-01]]
- [[Incidents-And-Lessons]]

---
## 📚 Study Connections
| Lab Concept | Exam Topic |
|---|---|
| VLAN topology (10/20/30/40/50/60) | [[VLAN-Concepts]] |
| pfSense firewall rules | [[Network-Security-Concepts]] |
| Suricata IDS on WAN | [[Network-Security-Concepts]] |
| Wazuh SIEM | [[Network-Security-Concepts]] |
| Tailscale VPN | [[Network-Security-Concepts]] |
| VLAN segmentation design | [[Subnetting-CIDR]] |
| HV-01/CL-01 Proxmox hypervisors | [[4.0-Virtualization-Cloud-Hub]] |
| Docker containers on SRV-01 | [[4.0-Virtualization-Cloud-Hub]] |
| intelux.local Active Directory | [[1.0-Operating-Systems-Hub]] |
| Network device registry | [[Network-Hardware]] |
| Kill Chain A/B exercises | [[Attack-Types]] |
| GRC change control docs | [[4.0-Operational-Procedures-Hub]] |
| Troubleshooting methodology used in sprints | [[Troubleshooting-Methodology]] |
