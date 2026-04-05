# 🖥️ INTELUX-HV-01 — Lenovo ThinkCentre M920t

**Updated:** 2026-04-05
**INTELUX Role:** Primary Hypervisor
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
| Model | Lenovo ThinkCentre M920t |
| CPU | Intel Core i5-8500 @ 3.0GHz (6C) |
| RAM | 16 GB DDR4 2400 MT/s (1x16GB Samsung — 3 slots open) |
| Storage | 476 GB NVMe SSD (PCIe, M.2 — 4 SATA ports fully open) |
| Max RAM | 64 GB |
| OS | Proxmox VE 8 |

---

## Hosted VMs

| INTELUX Name   | OS                  | Status               |
| -------------- | ------------------- | -------------------- |
| INTELUX-FW-01  | pfSense CE 2.7.2    | Active               |
| INTELUX-DC-01  | Windows Server 2022 | Active               |
| INTELUX-WEB-01 | Debian Linux        | Planned              |
| INTELUX-KSK-01 | Debian minimal      | Planned              |

---

## Upgrade Path

| Component | Action | Est. Cost | Priority |
|---|---|---|---|
| RAM | Add 1–3x 16GB DDR4 2400 → up to 64GB (3 slots open) | ~$35–50/stick | Medium |
| Storage | Add 3.5" SATA HDD(s) for VM storage expansion (4 SATA ports open) | ~$30–60/drive | Low |

---

## Notes

- NVMe boot drive on occupied M.2 slot — 4 SATA ports completely open for storage expansion
- Optical drive bay on SATA — replaceable with HDD for cheap bulk VM storage
- Facebook Marketplace acquisition — no setup issues

---

## Related Notes
- [[VM-Registry]]
- [[Trusted-Zone]]
- [[Lab-Architecture-Overview]]
- [[pfSense-Firewall]]