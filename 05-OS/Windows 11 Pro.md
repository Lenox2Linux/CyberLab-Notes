# 🪟 Windows 11 Pro

**Updated:** 2026-04-05 **Status:** Active — ADM-01 admin workstation

---

## Deployment

| Field       | Value                                         |
| ----------- | --------------------------------------------- |
| Host        | INTELUX-ADM-01 (ThinkPad T14)                 |
| Version     | Windows 11 Pro                                |
| VLAN        | 10 — MGMT                                     |
| Switch Port | SW-01 P6                                      |

---

## Role

Primary admin workstation for all INTELUX lab management tasks:

- pfSense web UI access
- Proxmox web UI access (HV-01, CL-01)
- Wazuh dashboard access
- Obsidian vault (this documentation)
- GitHub — `github.com/Lenox2Linux`
- ADM-01 also serves as personal laptop — dual-homing risk applies

---

## Security Notes

|Risk|Mitigation|
|---|---|
|Dual-homing (WiFi + Ethernet)|Disable WiFi before connecting ethernet during lab sessions|
|Personal + admin use on same device|Workflow discipline — separate personal from lab sessions|

---

## Known Wazuh Alert Patterns (ADM-01)

|Event ID|Cause|Classification|
|---|---|---|
|4672|Windows Update privilege assignment|False positive — documented|
|4738|Windows Update user account changes|False positive — documented|
|Mass FIM registry deletions — `HKLM\CurrentControlSet\Services\`|Windows Update cleanup|False positive — documented|

---

## Hardware Reference

See [[Lenovo ThinkPad T14 (Gen 2)]] for full hardware specs and upgrade path.

---

## Related Notes

- [[Trusted-Zone]]
- [[OS-Registry]]
- [[Lenovo ThinkPad T14 (Gen 2)]]
- [[Incidents-And-Lessons]]