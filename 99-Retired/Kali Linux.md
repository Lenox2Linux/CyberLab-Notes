# 🐉 Kali Linux

**Updated:** 2026-04-05 **Status:** Retired from INTELUX lab **Replaced By:** Parrot OS (bare-metal on RED-01)

---

> [!NOTE] Retired — Phase 0 Reference Kali Linux was the original red team OS used during Phase 0 of the lab. It has been fully replaced by Parrot OS on RED-01 (bare-metal). See [[INTELUX-RED-01-MacBookPro]] and [[RED-01-Build-History]] for current state.

---

## Phase 0 Role

|Field|Value|
|---|---|
|Host|MacBook Pro (2012) — via VirtualBox VM|
|Purpose|Controlled attack node inside isolated lab segment|
|Network|Double NAT isolated zone (192.168.1.x era)|
|Documented In|[[Kali Cyber Lab Rebuild]] (archived in `99-Retired`)|

---

## Why It Was Replaced

- VirtualBox VM overhead limited performance on aging hardware
- Full hardware dedication to red team ops required bare-metal install
- Parrot OS chosen for better stability and resource efficiency on MacBook Pro (2012)
- INTELUX STAGING VLAN (50) architecture made bare-metal the correct design choice

---

## Current Red Team OS

See [[Parrot OS]] and [[INTELUX-RED-01-MacBookPro]] for the current attack platform.

---

## Related Notes

- [[RED-01-Build-History]]
- [[INTELUX-RED-01-MacBookPro]]
- [[Isolated-Zone]]
- [[(Phase 0) Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation]]