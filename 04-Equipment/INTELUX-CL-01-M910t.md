# 🖥️ INTELUX-CL-01 — Lenovo ThinkCentre M910t

**Updated:** 2026-04-05
**INTELUX Role:** Victim/Client Hypervisor
**Status:** Active

---

## Acquisition

- **Source:** Facebook Marketplace
- **Form Factor:** Tower (Full)
- **No issues during acquisition or setup**

---

## Hardware Specifications

| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M910t |
| CPU | Intel Core i5-7500 @ 3.4GHz (4C) |
| RAM | 16 GB DDR4 2400 MT/s (1x16GB SK Hynix — 3 slots open) |
| Storage | 465 GB HDD (SATA 3.0 — 3 SATA ports open, 1 M.2 slot open) |
| Max RAM | 64 GB |
| OS | Proxmox VE 8 |

---

## Hosted VMs

| VM ID | INTELUX Name   | OS             | VLAN | IP          | Status               |
| ----- | -------------- | -------------- | ---- | ----------- | -------------------- |
| 102   | INTELUX-WKS-03 | Windows 10 Pro | 30   | 10.100.30.x | Active (powered off) |
| 103   | INTELUX-WKS-04 | Windows 10 Pro | 30   | 10.100.30.x | Active (powered off) |
| 200   | INTELUX-WKS-05 | Windows 10 Pro | 30   | 10.100.30.x | Planned              |
| 201   | INTELUX-WKS-06 | Windows 10 Pro | 30   | 10.100.30.x | Planned              |
| 250   | INTELUX-HNY-01 | TBD (Honeypot) | 50   | 10.100.50.x | Future               |

---

## Upgrade Path

| Component | Action | Est. Cost | Priority |
|---|---|---|---|
| Storage | Add M.2 NVMe → run Proxmox OS on NVMe, keep HDD for VM storage | ~$60–80 | HIGH |
| RAM | Add 16GB DDR4 2400 → 32GB (3 slots open) | ~$35–50 | Medium |
| Storage | Add additional SATA HDD/SSD (3 ports open) | ~$30–60 | Low |

> **Best upgrade:** M.2 NVMe for Proxmox OS speed, keep existing HDD for VM storage. Biggest bang for buck on this node.

---

## Notes

- Currently running HDD — NVMe upgrade would significantly improve VM performance
- 3 open SATA ports and 1 open M.2 slot — excellent expansion headroom
- Facebook Marketplace acquisition — no setup issues
- Dedicated to client/victim VMs for red team exercises

---

## Related Notes
- [[VM-Registry]]
- [[Trusted-Zone]]
- [[Lab-Architecture-Overview]]
- [[INTELUX-HV-01-M920t]]
