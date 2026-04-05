# 🍎 macOS 12 Monterey

**Updated:** 2026-04-05 **Status:** Retired — wiped from all lab machines

---

> [!NOTE] Retired — Phase 0 Reference macOS Monterey was the base OS on the MacBook Pro (2012) during Phase 0. It was fully wiped when RED-01 was rebuilt as a bare-metal Parrot OS machine. See [[RED-01-Build-History]] for the full rebuild timeline.

---

## Phase 0 Role

|Field|Value|
|---|---|
|Host|MacBook Pro (2012) — RED-01 predecessor|
|Purpose|Base OS hosting Kali Linux VM via VirtualBox|
|Network|Double NAT isolated zone (192.168.1.x era)|

### What Ran on It

- VirtualBox (hosted Kali Linux VM)
- macOS Terminal for `createinstallmedia` and disk prep
- Bootable USB creation for lab rebuilds

---

## Why It Was Retired

- macOS overhead unnecessary for a dedicated red team machine
- VirtualBox VM approach replaced by bare-metal install
- Full hardware control required for Parrot OS performance on MacBook Pro (2012)

---

## Current State of Host Machine

The MacBook Pro (2012) that ran Monterey is now RED-01 running Parrot OS bare-metal on VLAN 50 STAGING.

See [[INTELUX-RED-01-MacBookPro]].

---

## Related Notes

- [[RED-01-Build-History]]
- [[INTELUX-RED-01-MacBookPro]]
- [[Kali Linux]]