# 💻 INTELUX-ADM-01 — Lenovo ThinkPad T14 (Gen 2)

**Updated:** 2026-04-05
**INTELUX Role:** Admin Workstation
**Status:** Active

---

## Overview

The ThinkPad T14 is the primary admin workstation for all INTELUX lab management. It also serves as a daily driver for school and personal use when not in a lab session. Dual-homing risk applies — see security notes below.

---

## Hardware Specifications

| Field | Value |
|---|---|
| Model | Lenovo ThinkPad T14 (Gen 2) — 20XLS09L00 |
| CPU | AMD Ryzen 7 PRO 5850U (8C/16T) |
| RAM | 16 GB DDR4 3200 MT/s (1x16GB SO-DIMM + 8GB soldered = 24GB? — verify) |
| Storage | 512 GB NVMe (ADATA LEGEND 710, PCIe 3.0) |
| Max RAM | 48 GB (add 32GB SO-DIMM → 40GB usable + 8GB soldered) |
| OS | Windows 11 Pro |
| Upgrades | None yet |

---

## Network

| Field | Value |
|---|---|
| VLAN | 10 — MGMT |
| IP | 10.100.10.100 |
| Switch Port | SW-01 P6 |
| Old IP (Phase 0) | 192.168.1.69 |

---

## Wazuh Agent

| Field | Value |
|---|---|
| Agent ID | 008 |
| Agent Name | ADM-01 |
| Groups | ADMIN, windows |
| Status | Active |

---

## Daily Use

| Context | Use |
|---|---|
| Lab sessions | pfSense UI, Proxmox UI, Wazuh dashboard, SSH to SRV-01 |
| Documentation | Obsidian vault, GitHub pushes |
| School | Coursework, WCC portal, research |
| Personal | General use when not in lab session |

---

## Security Notes

| Risk | Detail | Mitigation |
|---|---|---|
| Dual-homing | T14 connects to both home WiFi and INTELUX ethernet | Disable WiFi before connecting ethernet during lab sessions |
| Personal + admin on same device | Same machine used for lab management and personal tasks | Workflow discipline — never mix sessions |

---

## Known Wazuh Alert Patterns

| Event | Cause | Classification |
|---|---|---|
| 4672 | Windows Update privilege assignment | False positive — documented |
| 4738 | Windows Update user account changes | False positive — documented |
| Mass FIM deletions — `HKLM\CurrentControlSet\Services\` | Windows Update cleanup | False positive — documented |

---

## Upgrade Path

| Component | Action | Est. Cost | Priority |
|---|---|---|---|
| RAM | Add 32GB SO-DIMM → ~40GB total | ~$55–75 | Low — current spec adequate |
| Storage | 512GB NVMe sufficient for now | — | Low |

---

## Related Notes
- [[Trusted-Zone]]
- [[Windows 11 Pro]]
- [[OS-Registry]]
- [[Equipment-Inventory]]
