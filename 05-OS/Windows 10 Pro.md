# 🪟 Windows 10 Pro

**Updated:** 2026-04-05 **Status:** Active — victim/target VMs

---

## Overview

Windows 10 Pro is the OS deployed across all victim workstation VMs in the INTELUX lab. These machines serve as targets for red team exercises and SOC detection practice.

---

## Active Deployments

| INTELUX Name   | VM ID        | Host  | VLAN | Status               |
| -------------- | ------------ | ----- | ---- | -------------------- |
| INTELUX-WKS-03 | 101 on HV-01 | M920t | 30   | Active (powered off) |
| INTELUX-WKS-04 | 102 on HV-01 | M920t | 30   | Active (powered off) |
| INTELUX-WKS-05 | 200 on CL-01 | M910t | 30   | Planned              |
| INTELUX-WKS-06 | 201 on CL-01 | M910t | 30   | Planned              |

---

## Role in Lab

- **Kill Chain A target:** WKS-03 (10.100.30.x) — nmap SYN scan from RED-01 in progress
- **Kill Chain B:** WKS-04, WKS-05, WKS-06 — future victim endpoints
- All VMs on VLAN 30 CLIENTS
- Wazuh agents enrolled to SRV-01 manager (10.100.20.xxx)
- VMs are powered off when not in use to conserve HV-01 and CL-01 resources

---

## Wazuh Alert Patterns (Known False Positives)

|Event|Explanation|
|---|---|
|Event 4672|Windows Update / privilege assignment — not intrusion|
|Event 4738|Windows Update user account changes — not intrusion|
|Mass FIM registry deletions under `HKLM\CurrentControlSet\Services\`|Windows Update cleanup — expected pattern|

---

## Previous Phase 0 Role

In Phase 0, Windows 10 Pro ran as a VirtualBox VM on the Mac mini (2014) with dual network adapters (NAT + Internal Network) for micro-segmentation practice. That setup has been replaced by the current Proxmox VM architecture.

---

## Related Notes

- [[VM-Registry]]
- [[Trusted-Zone]]
- [[OS-Registry]]
- [[Incidents-And-Lessons]]