# 💻 INTELUX-ADM-01 — AceMagic Mini PC

**Updated:** 2026-04-14
**INTELUX Role:** Admin Workstation (ADM)
**Status:** Active

---

## Overview

ADM-01 is the primary administration workstation for all INTELUX lab management. Replaced the ThinkPad T14 (Gen 2) on 2026-04-14. Dedicated MGMT node — no dual-homing risk. Obsidian vault and GitHub operations run locally on this machine.

---

## Hardware Specifications

| Field   | Value                             |
|---------|-----------------------------------|
| Model   | AceMagic Mini PC                  |
| CPU     | AMD Ryzen 7 6800H (8C/16T)       |
| RAM     | 30GB DDR5 + 24GB Swap             |
| Storage | 476.9GB NVMe SSD                  |

---

## Network

| Field       | Value          |
|-------------|----------------|
| Hostname    | intelux-adm-01 |
| User        | itadmin        |
| VLAN        | 10 — MGMT      |
| Switch Port | SW-01          |

---

## Software

| Component   | Detail                          |
|-------------|---------------------------------|
| OS          | Debian GNU/Linux 13 (Trixie)    |
| Kernel      | 6.12.74+deb13+1-amd64           |
| Browser     | Firefox ESR (local CA imported) |
| Vault       | Obsidian (local)                |

---

## Wazuh Agent

| Field      | Value          |
|------------|----------------|
| Agent ID   | 017            |
| Agent Name | intelux-adm-01 |
| Group      | ADMIN          |
| Status     | Active         |

---

## Daily Use

| Context      | Use                                                     |
|--------------|---------------------------------------------------------|
| Lab sessions | pfSense UI, Proxmox UI, Wazuh dashboard, SSH to SRV-01 |
| Documentation| Obsidian vault, GitHub pushes                           |
| School       | Coursework, WCC portal, research                        |

---

## Security Notes

| Risk                    | Detail                            | Mitigation                            |
|-------------------------|-----------------------------------|---------------------------------------|
| Dedicated MGMT node     | No dual-homing — dedicated device | Risk resolved vs. T14                 |
| Privileged admin access | Full lab management capability    | Wazuh agent 017 monitors all activity |

---

## Change Log

| Date       | Change                                     | Author |
|------------|--------------------------------------------|--------|
| 2026-04-14 | Node commissioned as ADM-01, replacing T14 | RAP    |

---

## Related Notes
- [[Trusted-Zone]]
- [[Equipment-Inventory]]
- [[Wazuh-SIEM]]
- [[OS-Registry]]
