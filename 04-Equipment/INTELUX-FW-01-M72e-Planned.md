# 🔥 INTELUX-FW-01 (Planned Bare-Metal) — Lenovo ThinkCentre M72e

**Updated:** 2026-04-05
**INTELUX Role:** pfSense Bare-Metal Firewall (Phase 2)
**Status:** Incoming — Arriving 04/07/26

---

## Acquisition

- **Source:** Mercari (USSF listing)
- **Condition:** Used

---

## Hardware Specifications

| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M72e |
| RAM | 12 GB DDR3 |
| Storage | 120 GB SSD |
| Current OS | TBD — will be wiped for pfSense CE |

---

## Network Interface Plan

| NIC | Source | Role |
|---|---|---|
| Onboard NIC | Built-in | LAN interface |
| Realtek USB NIC | Repurposed from HV-01 | WAN interface |

> The Realtek USB NIC currently in use on HV-01 will be moved to M72e as the WAN interface when deployment begins.

---

## Deployment Plan

### Phase 2 Migration Steps
1. Receive M72e — confirm POST and hardware health
2. Flash pfSense CE installer to USB
3. Install pfSense CE bare-metal
4. Configure LAN (onboard NIC) and WAN (Realtek USB NIC)
5. Migrate existing pfSense config (export XML from current VM)
6. Import config to bare-metal pfSense
7. Test all 6 VLANs, firewall rules, Suricata, DHCP
8. Decommission pfSense VM (VM 100) on HV-01
9. Reclaim HV-01 resources from pfSense VM

### Benefits of Bare-Metal Migration
- Removes VM overhead for core firewall
- Dedicated hardware = more reliable WAN failover
- Frees HV-01 VM resources for additional lab VMs
- Cleaner architecture — firewall not dependent on hypervisor uptime

---

## Current pfSense (Pre-Migration Reference)

| Field | Value |
|---|---|
| Current Host | VM 100 on HV-01 |
| pfSense Version | CE 2.7.2 |
| vCPU | 2 |
| vRAM | 4 GB |
| Virtual Disk | 32 GB |
| Interfaces | vmbr0 / vmbr1 |

---

## Notes

- Config XML backup saved (Step2 XML) — use for migration import
- Do not begin migration until M72e hardware is verified stable
- Suricata rules and EVE JSON pipeline must be re-validated post-migration
- Tailscale subnet router on SRV-01 must be verified post-migration

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[INTELUX-HV-01-M920t]]
- [[Trusted-Zone]]
- [[Incidents-And-Lessons]]
