# 🌿 Linux Mint

**Updated:** 2026-04-05 **Status:** Retired — no current role in INTELUX lab

---

> [!NOTE] Retired — Phase 0 Reference Linux Mint was used briefly during Phase 0 as a general-purpose Linux VM. It has no active role in the current INTELUX architecture. All Linux workloads are now handled by Ubuntu 24.04 (SRV-01) and Parrot OS (RED-01).

---

## Phase 0 Role

|Field|Value|
|---|---|
|Host|VirtualBox VM (Mac mini 2014 or MacBook Pro 2012)|
|Purpose|General-purpose Linux desktop / administration|
|Network|Flat 192.168.1.x|

---

## Current Linux Deployments

|Host|OS|Role|
|---|---|---|
|SRV-01|Ubuntu 24.04 LTS|Docker services host|
|RED-01|Parrot OS|Red team attack platform|
|HV-01|Proxmox VE 8 (Debian base)|Hypervisor|
|CL-01|Proxmox VE 8 (Debian base)|Hypervisor|

---

## Related Notes

- [[OS-Registry]]
- [[INTELUX-SRV-01-MacMini]]
- [[INTELUX-RED-01-MacBookPro]]