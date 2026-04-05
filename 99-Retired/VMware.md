> [!NOTE] Retired — Phase 0 Reference Oracle VirtualBox was the hypervisor platform used during Phase 0 of the lab. It has been fully replaced by Proxmox VE on HV-01 (M920q) and CL-01 (M910q). See [[VM-Registry]] for the current VM infrastructure.

---

# Oracle VirtualBox — Phase 0 Hypervisor

**Updated:** 2026-04-05 **Status:** Retired — replaced by Proxmox VE

---

## Phase 0 Role

|Field|Value|
|---|---|
|Host|Mac mini (2014)|
|Purpose|Primary virtualization platform|
|VMs Hosted|Ubuntu 22.04, Windows 10 Pro|
|Network|Dual adapter — NAT + Internal Network|

### What Ran on It

- Ubuntu VM — administration and monitoring
- Windows 10 Pro VM — victim/target endpoint
- Dual network adapters for micro-segmentation practice
- Static IP addressing on internal network segment

---

## Why It Was Replaced

|VirtualBox|Proxmox VE|
|---|---|
|Desktop hypervisor — not enterprise grade|Type 1 bare-metal hypervisor|
|Limited VM management|Full web UI, API, clustering|
|No VLAN support|Native VLAN tagging via Linux bridge|
|Single host|Two dedicated hypervisor nodes (HV-01, CL-01)|
|No snapshot scheduling|Built-in backup and snapshot management|

---

## Current Hypervisor Platform

|Node|Hardware|Role|
|---|---|---|
|HV-01|Lenovo M920q|Primary hypervisor — pfSense, WKS-03, WKS-04, DC-01|
|CL-01|Lenovo M910q|Client hypervisor — WKS-05, WKS-06, HNY-01|

See [[VM-Registry]] and [[INTELUX-HV-01-M920t]] and [[INTELUX-CL-01-M910t]].

---

## Related Notes

- [[VM-Registry]]
- [[INTELUX-HV-01-M920t]]
- [[INTELUX-CL-01-M910t]]
- [[(Phase 0) Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation]]